---
title: "MySQL won't start"
date: 2013-05-24
forum: Mythbuntu
---

### Post by philled on 2013-05-24
I had a power outage and ever since I've been unable to start the MySQL daemon. I have these errors in /var/log/mysql/error.log:

[FONT=fixedsys]130524 20:07:43 [Note] Plugin 'FEDERATED' is disabled.
130524 20:07:43 InnoDB: The InnoDB memory heap is disabled
130524 20:07:43 InnoDB: Mutexes and rw_locks use GCC atomic builtins
130524 20:07:43 InnoDB: Compressed tables use zlib 1.2.3.4
130524 20:07:43 InnoDB: Initializing buffer pool, size = 128.0M
130524 20:07:43 InnoDB: Completed initialization of buffer pool
130524 20:07:43 InnoDB: highest supported file format is Barracuda.
InnoDB: The log sequence number in ibdata files does not match
InnoDB: the log sequence number in the ib_logfiles!
130524 20:07:43  InnoDB: Database was not shut down normally!
InnoDB: Starting crash recovery.
InnoDB: Reading tablespace information from the .ibd files...
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
130524 20:07:43  InnoDB: Waiting for the background threads to start
130524 20:07:44 InnoDB: 5.5.31 started; log sequence number 72354077
130524 20:07:44  InnoDB: Assertion failure in thread 140690101622528 in file fut0lst.ic line 83
InnoDB: Failing assertion: addr.page == FIL_NULL || addr.boffset >= FIL_PAGE_DATA
InnoDB: We intentionally generate a memory trap.
nnoDB: Failing assertion: addr.page == FIL_NULL || addr.boffset >= FIL_PAGE_DATAInnoDB: Submit a detailed bug report to [http://bugs.mysql.com](http://bugs.mysql.com).
InnoDB: If you get repeated assertion failures or crashes, even
InnoDB: immediately after the mysqld startup, there may be
InnoDB: corruption in the InnoDB tablespace. Please refer to
InnoDB: [http://dev.mysql.com/doc/refman/5.5/en/forcing-innodb-recovery.html](http://dev.mysql.com/doc/refman/5.5/en/forcing-innodb-recovery.html)
InnoDB: about forcing recovery.
10:07:44 UTC - mysqld got signal 6 ;
This could be because you hit a bug. It is also possible that this binary
or one of the libraries it was linked against is corrupt, improperly built,
or misconfigured. This error can also be caused by malfunctioning hardware.
We will try our best to scrape up some info that will hopefully help
diagnose the problem, but since we have already crashed,
something is definitely wrong and this may fail.

key_buffer_size=16777216
read_buffer_size=131072
max_used_connections=0
max_threads=100
thread_count=0
connection_count=0
It is possible that mysqld could use up to
key_buffer_size + (read_buffer_size + sort_buffer_size)*max_threads = 4945524 K  bytes of memory
Hope that's ok; if not, decrease some variables in the equation.

Thread pointer: 0x0
Attempting backtrace. You can use the following information to find out
where mysqld died. If you see no messages after this, something went
terribly wrong...
stack_bottom = 0 thread_stack 0x30000
130524 20:07:44 [Note] Server hostname (bind-address): '0.0.0.0'; port: 3306
130524 20:07:44 [Note]   - '0.0.0.0' resolves to '0.0.0.0';
130524 20:07:44 [Note] Server socket created on IP: '0.0.0.0'.
/usr/sbin/mysqld(my_print_stacktrace+0x29)[0x7ff50f30a7b9]
/usr/sbin/mysqld(handle_fatal_signal+0x483)[0x7ff50f1d08f3]
/lib/x86_64-linux-gnu/libpthread.so.0(+0xfcb0)[0x7ff50df1dcb0]
/lib/x86_64-linux-gnu/libc.so.6(gsignal+0x35)[0x7ff50d589425]
/lib/x86_64-linux-gnu/libc.so.6(abort+0x17b)[0x7ff50d58cb8b]
/usr/sbin/mysqld(+0x5b4dba)[0x7ff50f369dba]
/usr/sbin/mysqld(+0x5b55a5)[0x7ff50f36a5a5]
/usr/sbin/mysqld(+0x67b5af)[0x7ff50f4305af]
/usr/sbin/mysqld(+0x671b05)[0x7ff50f426b05]
/usr/sbin/mysqld(+0x5b747e)[0x7ff50f36c47e]
/usr/sbin/mysqld(+0x5a835c)[0x7ff50f35d35c]
/usr/sbin/mysqld(+0x5ac793)[0x7ff50f361793]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x7e9a)[0x7ff50df15e9a]
/lib/x86_64-linux-gnu/libc.so.6(clone+0x6d)[0x7ff50d646ccd]
The manual page at [http://dev.mysql.com/doc/mysql/en/crashing.html](http://dev.mysql.com/doc/mysql/en/crashing.html) contains
information that should help you find out what is causing the crash.
[/FONT]
I'm wondering whether MySQL got corrupted when the power outage occurred. Does anyone know how to recover from something like this?

---

### Post by Rotak on 2013-05-25
There is a tool calles "mysqlrepair", which may help you. Check the "--help" output. I guess "-c" (check), and "-r" (repair) are the most interesting parameters for you. ;)

---

### Post by josephmills on 2013-05-25
what happens if you stop the backend start mysql and then restart the backend ?  
```
sudo service mythbackend stop 
```
```
sudo service mysql start 
```
```
sudo service mythbackend start 
```

thanks

---

### Post by philled on 2013-05-27
I think I've found the solution to this. It turns out to be a Cixtrix XenServer issue (sorry, in hindsight I should have posted it to a different forum).

I removed the storage respositories from XenServer as per [CTX131328 - How to Remove a Storage Repository from XenServer - Citrix Knowledge Center]("http://support.citrix.com/article/CTX131328"). 

I then followed the instructions at [CTX121896 - How to Introduce a Local Storage Repository in XenServer - Citrix Knowledge Center]("http://support.citrix.com/article/CTX121896") to re-introduce the storage repositories. I reattached them to the Mythbuntu VM and it then booted up fine.

So definitley a XenServer issue, I think. Hope this helps someone else in the future.

---

