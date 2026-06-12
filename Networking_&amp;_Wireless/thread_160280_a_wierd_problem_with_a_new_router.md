---
title: "a wierd problem with a new router"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2006-04-14
I bought a new router (Safecom GWART2-54125/SWART2-54125) to replace my old Origo. Now I cannot browse Internet with Firefox. Also apt-get also does not have any connection.

I can ping sites without any problem. Gaim connects to ICQ and Yahoo networks but not to MSN.

I followed the guide [here]("http://www.ubuntuforums.org/showthread.php?t=87643") and everything seems fine. But still I cannot browse internet. Thunderbird also does not work.

I booted in Windows and everything there works fine. I have no idea what to do. If anyone could help me I would be very grateful.

---

### Post by slipk487 on 2006-04-14
u need to reconfigure the ip address windows does it automaticly but ubuntu u have to do it manuly

---

### Post by foxy123 on 2006-04-14
[QUOTE=slipk487]u need to reconfigure the ip address windows does it automaticly but ubuntu u have to do it manuly[/QUOTE]
how can I do it?

---

### Post by foxy123 on 2006-04-14
another thing: I tried live CDs. With Knoppix Internet works fine but with Ubuntu (both Breezy and Dapper Flight 6) no luck.

---

### Post by slipk487 on 2006-04-14
i have a program called configure network card and dont rember were i got it but try running this

```
sudo xnetcardconfig
```

---

### Post by foxy123 on 2006-04-14
it's getting wierder and wierder... firefox works ok now, but apt-get and thunderbird do not...
```
$ sudo apt-get install xnetcardconfig
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gnome-bin gnome-libs-data libart2 libatk1-ruby libgdk-pixbuf2-ruby
  libglib2-ruby libgnome32 libgnomesupport0 libgnomeui32 libgnorba27
  libgnorbagtk0 libgtk2-ruby liborbit0 libpango1-ruby libruby1.8 libzvt2 pump
  ruby ruby1.8 xsu
Suggested packages:
  gnome-core resolvconf ruby1.8-examples rdoc1.8 ri1.8 menu xfld-welcome
The following NEW packages will be installed:
  gnome-bin gnome-libs-data libart2 libatk1-ruby libgdk-pixbuf2-ruby
  libglib2-ruby libgnome32 libgnomesupport0 libgnomeui32 libgnorba27
  libgnorbagtk0 libgtk2-ruby liborbit0 libpango1-ruby libruby1.8 libzvt2 pump
  ruby ruby1.8 xnetcardconfig xsu
0 upgraded, 21 newly installed, 0 to remove and 1 not upgraded.
Need to get 3624kB of archives.
After unpacking 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Connecting to gb.archive.ubuntu.com (1.0.0.0)]

```
why is it trying to connect to 1.0.0.0?

---

### Post by slipk487 on 2006-04-14
thats weird so apt-get wont connect to the internet to download the files ive never seen that happen before ill check into it and see if i can figure it out

---

### Post by mips on 2006-04-14
Have a look at IPv6 & DNS.

---

### Post by foxy123 on 2006-04-14
[QUOTE=mips]Have a look at IPv6 & DNS.[/QUOTE]
i've got a suspicion that it has something to do with my problem but alas, I am not very good in networking things :( any advice where to look at?

---

### Post by foxy123 on 2006-04-15
ok, here is the solution. I entered manuallly DNS and Gateway addresses in the router and it works fine now. I wonder why Ubuntu could not recognise default settings?

---

