# test

## tip：
	一行-->记录
	一列-->字段
	where 1=1 --->保证语句正确可执行，后面的条件是ture的话，则会自动and，后面的结果为false的话就查询整个表

## 三范式
	1NF：一条记录对应一个实例
	2NF：主键唯一
	3NF：别的表已有，这个表不应再加入该字段（非主键）

## 登录：mysql -u用户名 -p密码(不加分号)
进入一个数据库: use 数据库名;
查看数据表格：show tables;


创建用户：create user '用户名' identified by '密码';
删除用户： drop user '用户名';
修改密码：set password for '用户名'@'host值' = '新密码';
授权：授予全部权限：grant all on *.* to '用户名' @ 'host值'; <-- 在mysql数据库中，查看user表可知


## 查询语句：
	1.select：
		select [distinct] {字段 (别名)|表达式}               tip:字段+null 就变 null-->字段+IFNULL（字段，替换值）  防止加完都变成null
		from 表名 (别名)---->可以嵌套一个select
		where 条件 ------------------------------------>1.=、 >、 <、 <= 、>=、 !=、 <>（不等于）、 between ... and ...
		order by [asc|dsc]					     2.and、or、not
									     3.is null、字段 is not null (not 字段 is null )
									     4.like：模糊查询-->like  '%特征%'   '_A%'第二位是A	
									     5.in、exist、子查询-->where 字段 in (10,20,30)
													exists 后面的语句有结果（true），则执行前面的语句
									     6.union(并集)、intersect（交集）--->用于两个select语句之间


数字函数：
	select abs(n)   求绝对值
	select mod(10,3)  取余
	select floor(n)  向下取整
	select celling(n) 向上取整
	select round(n) 四舍五入
	....   pow(x,y) x的y次方
	... PI() 圆周率
	... rand()  0-1之间的随机数

流程控制：
	select 字段
	case
	when 条件 then 操作
	else 操作
	end as 新字段名
	from 表

组函数：
	count() 多少条记录------> select count(*/主键) from 表 ++ 不会统计值为null的记录

	max/min() ------>SELECT * from user
			      where 1=1 and age=(
				SELECT max(age) from user
			       );
	sum()
	avg()

分组/过滤组：
	select [distinct] {字段 (别名)|表达式}               
	from 表名 (别名)
	where 条件 
	group by --->分组
	having --->过滤组
	order by [asc|dsc]		

连接查询
	交叉连接（外连接） cross join

	内连接： inner join	  -------------->会查出两个表对等的记录（交集）
		select 字段 from 表 inner join 表2 on 表1.字段=表2.字段

	外连接： -------------------------->会查出两个表的交集以及主表的记录（左外就是左边的是主表）
		    1.左外连接：left join	
		    2.右外连接：right join

分页：select .. from ... limit 0,5;------------->从0开始，选5条记录作为一页



索引：
	create 




