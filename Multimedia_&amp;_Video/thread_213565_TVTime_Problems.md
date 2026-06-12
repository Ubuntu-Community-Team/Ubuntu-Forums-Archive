---
title: "TVTime Problems"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by hellmet on 2006-07-11
Dear all,
It never happened like this before..
I installed Tvtime yesterday after installing
Dapper clean after breakin the previous install
Tvtime no longer can open the stationlist..saying it 
needs some permissions..

If i open tvtime in the terminal as
sudo tvtime

it works perfectly..

Can I do something about it so that 
it accesses the stationlist normally??

---

### Post by whatever on 2006-07-11
check the permissions of ~/.tvtime/stationlist.xml

---

### Post by hellmet on 2006-07-11
it seems like I don't have the right to open any Program 
with root permissions...
I mean...I need to manually type sudo for virtually every program
to make them run!!!

any idea as to what I shud do here??

---

### Post by christooss on 2006-07-11
try

sudo chown -R username:username ~/.tvtime

---

### Post by hellmet on 2006-07-12
who..i didn't understnad a word of the command..
but it worked like charm!!
thnkx man..
Anyway I am plannin to reinstall
I can see too many problems with the current Dapper install
Will have to do a clean install again

---

### Post by christooss on 2006-07-12
sudo - super user do - it gives user root permisions

chown - changes user and group

-R - does change recursevly

username:username - first one is User and second one is User Group. Same name but different :)

~/.tvtime - is dir with settings

---

### Post by hellmet on 2006-07-12
whoa..thanks for tat again..

---

