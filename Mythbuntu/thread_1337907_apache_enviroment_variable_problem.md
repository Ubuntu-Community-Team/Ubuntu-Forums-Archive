---
title: "apache enviroment variable problem?"
date: 2009-11-25
forum: Mythbuntu
---

### Post by C_Oblender on 2009-11-25
Encountered a somewhat frustrating problem while I was testing a cgi script that I wrote for mythnettv.  It calls mythnettv and directs its output to /var/tmp. It then reads that file and uses the data to create a simple browser interface.  Works great outside of apache. Falls flat on its face when it calls mythnettv.

The error log shows:
```
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1] Traceback (most recent call last):
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1]   File "/usr/share/mythnettv/mythnettv", line 596, in <module>
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1]     
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1] main(sys.argv)
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1]   File "/usr/share/mythnettv/mythnettv", line 198, in main
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1]     
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1] db = database.MythNetTvDatabase()
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1]   File "/usr/share/mythnettv/database.py", line 55, in __init__
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1]     
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1] dbhost=dbhost)
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1]   File "/usr/share/mythnettv/database.py", line 91, in OpenConnection
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1]     
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1] if os.path.exists(home + '/.mythtv/mysql.txt'):
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1] TypeError
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1] : 
[Wed Nov 25 16:31:47 2009] [error] [client 127.0.0.1] unsupported operand type(s) for +: 'NoneType' and 'str'

```It is apparent from the error messages that part of mythnettv needs the HOME environment variable but it must not exist in apache's environment.  How would one work around this?

Edit:

I feel so stupid now. I solved my problem by adding the line:

```
os.environ['HOME'] = '/var/www'
```

to my cgi script.  This naturally is passed to mythnettv and every things happy.

---

