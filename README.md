mysql-tcl
=========

A forked code from mysqltcl-3.052 -- A Tcl implementation of MySql client library


```
package require mysqltcl

set mysql [mysql::connect -host $host -user $user -password $passwd -db $db]

mysql::use $mysql $db

foreach row [mysql::sel $mysql {SELECT * FROM my_table} -list] {
  lassign $row col_1 col_2 col_3
}

foreach {col_1 col_2 col_3} [mysql::sel $mysql {SELECT * FROM my_table} -flatlist] {
  # ...
}

mysql::exec $mysql {UPDATE ...}

set query [mysql::query $mysql {SELECT * FROM my_table WHERE id=3}

mysql::map $query {col_1 - col_3} {
  puts $col_1
}

mysql::endquery $query

mysql::receive $mysql {
  SELECT * FROM my_table where id=3
} {col_1 - col_3} {
  puts $col_1
}
```


