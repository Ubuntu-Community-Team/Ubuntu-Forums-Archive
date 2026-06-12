---
title: "Trying to install  mythstream on 9.10"
date: 2009-12-31
forum: Mythbuntu
---

### Post by benlyboy on 2009-12-31
Hi was hoping some can help


Have been trying to install mythstream using this blog [http://dougaus.blogspot.com/2009/12/installing-mystream-on-mythbuntu-910.html](http://dougaus.blogspot.com/2009/12/installing-mystream-on-mythbuntu-910.html)
as a guide.

Everything seemed to go ok, until I got to the fourth line (qmake mythstream.pro) at which point I got this message (cannot find file: mythstream.pro.)

I was hoping that someone a lot smarter than I could tell me if the author of this blog  has made a typo or am I doing something wrong?

My system is running mythbuntu 9.10 (64)

Thanks for any help....:P

---

### Post by Singing Dwarf on 2010-01-08
I followed these instructions and got the same error message as you.  There is a way around it though.

Before the step ```
qmake mythstream.pro
```you will need to

```
cd mythstream_mythtv-r21640.tar.gz
```I also had to 

```
sudo apt-get install g++
```before running qmake mythstream.pro

---

### Post by copycat on 2010-01-13
Good topic!

It works for me... 

It only should be

"**cd mythstream_mythtv-r21640**"  and not "cd mythstream_mythtv-r21640.tar.gz"

I suppose.

:popcorn:



Only adding a mp3 stream from our local radio gives **invalid url**.  Any suggestions?

---

### Post by jimbolaya on 2010-03-25
I tried compiling this but ended up with a long list of problems.  I attempted to fix most of them by trying the g++ line manually and adding -I statements, but I still ended up with a pile of errors.

Has much changed since January?

---

### Post by modorf on 2010-05-17
When I was compiling mythstream for MythTV 0.24, 
I needed to add the package libexpat1-dev

---

### Post by geekyhawkes on 2010-05-18
Very interesting thread, has anyone managed to get mythstream working on .22?

---

### Post by modorf on 2010-11-03
found further information on building mythstream for MythTV 0.24

patch files from MiniMyth project for mythstream
[http://minimyth.googlecode.com/svn/trunk/gar-minimyth/script/myth-0.24/mythstream/]("http://minimyth.googlecode.com/svn/trunk/gar-minimyth/script/myth-0.24/mythstream/")

found source files through this thread from mythtv user list: [http://www.gossamer-threads.com/lists/mythtv/users/457750]("http://www.gossamer-threads.com/lists/mythtv/users/457750")

---

