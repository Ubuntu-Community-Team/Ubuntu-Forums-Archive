---
title: "Sam Broadcaster error in Ubuntu Karmic.. Please HELP !"
date: 2009-12-17
forum: Multimedia Software
---

### Post by alexdej on 2009-12-17
Hey. So I installed Sam Broadcaster with Wine's help to be a DJ on linux, and all installed nice, I checked the songs with the player's database - FireBird, and I rebooted my pc. When I tried to start Sam Broadcaster again, I get this errors :
"Unable to connect or query database. Please make sure the database server is running and configured properly." & "Connection to database failed".
Strange thing is that, the database server is On, and still doesn't work..
2610 ?        Ssl    0:00 C:\Program Files\Firebird\Firebird_2_1\bin\fbserver.exe                                      
 2623 ?        Ssl    0:00 C:\Program Files\Firebird\Firebird_2_1\bin\fbguard.exe                                      
I tried to start the program from the terminal too.. and I got this :
jack@Jack:~/sam 4$ wine SAMBC.exe
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:ALSA_ComputeCaps failed: Invalid argument(-22)
fixme:msxml:DllCanUnloadNow 
jack@Jack:~/sam 4$ 
Graphically, with the same database error..
Can anybody help me please ?

---

