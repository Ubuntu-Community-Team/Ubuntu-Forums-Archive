---
title: "Vuescan...am I being stupid?"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by kathrync on 2008-03-14
Ok, so I'm new to Linux and you'll have to excuse me if I am being really stupid.

I am trying to get my scanner going (Epson Perfection v200 photo).  I have managed to download and install the drivers and it is working fine with XSANE.

However, I was using Vuescan on Windows and liked it a lot so I figure I may as well keep using it on Ubuntu.  I downloaded it fine (demo version) and extracted it but I am not sure what is going on now.  I downloaded it and extracted it to my desktop so I could see everything.  When I extract it, I get a load of the usual files (splash pages, .dat files etc) and also an executable file.  When I double click on the executable it will open and work fine.  But I don't seem to have installed it.  What I mean is that every other time I have downloaded and installed something (Google Earth, Skype etc), everything has been moved automatically to sensible places in the /usr folder whereas this time everything is still scattered randomly over my desktop.  I don't really want them there (I am a bit anal about having a tidy desktop!) and I am reluctant to start moving stuff about randomly because I am bound to lose something!

So, have I done something stupid?  Or is this just how vuescan works in Linux?  Would I be better to re-extract to somewhere more out of the way or is there some way of installing it properly?  I have tried everything I know (all manual, it doesn't show up in Synaptic....).

Many thanks!

Kathryn

---

### Post by kathrync on 2008-03-16
Bump

Anyone??

---

### Post by apos on 2008-04-21
No you are not ;)
Your question's kept me smiling a little bit - but it's OK ;)
And &#347;ince this is a very popular program, i will explain:

So, in fact it's very easy: What you downloaded from *hamrick.com* was a simple packed file (like a zip). 
This file contains 
[LIST]
[*]the programm executable (*vuescan*)
[*]a data file (*vuescan.dat*)
[/LIST]
and some other files (*help files* for the browser and a *splash screen bitmap*). 

You should have learned: a "program" like *vuescan* has more than one part to function properly, but - mostly - just ONE *executable*.

To **run** the program - and in fact **every linux executable**
[LIST]
[*]you double klick it OR
[*]edit a custom starter e.g. in your gnome panel that contains the executable with the whole program path (e.g. */home/username/vuesca84/vuescan*)
[*]run it from a terminal
[/LIST]

Therefore, the executable has to have the execute bit set
```
chmod 750 program
```
This is the case, because *hamrick.com* did this for you and delivers the folder packed with a linux compatible packer (tar).

How to **install** a / the program - and in fact **every linux executable** - depends what the developer decided. There are a lot of options.

Usually under linux a program is delivered packaged for your special linux flavour e.g in a debian package or a rpm package. This package in conjunction with the package manager (synaptic, apt, ...) keeps care for delivering the different program parts into defined places, executable in */usr/bin,* settings in */etc* and/or your home directory, data in */usr/share/programname*, creating a menu entry for you, upgrading a previously installed package with a lower version... - shortly: you don't have to care about all that.

[B]In case of *vuescan,* this is a very simple program delivery concept that is NOT managed by your linux distribution or package manager (synaptic). That's very easy for the developer, but bad for the user experience.
[/B]
All program parts are designed to run in ONE directory. Probably you should write an email to hamrick.com and ask for a ubuntu package - the more people are demanding packaged versions for linux, the more likely we get little buttons "download" for ubuntu/suse/redhat/... ;)

It is now up to you putting the whole *program directory* into a folder of your choice and find a way to run it by creating e.g. a *custom panel/menu entry*.

**I recommend** putting the vuescan dir into your homefolder. Probably by putting a "dot" in front of it, so it will not be visible.
```
cp -av /home/username/Desktop/vuesca84 /home/username/.vuesca84
```

**Another way ** - and this will enable the usage of the program by anyone on the pc easily - is putting it into e.g. */usr/local/share* (with sudo)
```
sudo cp -av /wherever/vuesca84  /usr/local/share/.
```

Then make a symbolic link into /usr/bin:
```
cd /usr/bin
sudo ln -s /usr/local/share/vuescan84/vuescan vuescan

```

Because the directory */usr/bin* will be searched for executables first, you are able to run the program by simply using *vuescan* instead of the whole program path, either in a terminal, or panel/desktop starter, Alt+F2, etc.

Now have fun. Probably you have to google around a little bit about *installing custom programs into linux*. AND again: write an email to *hamrick.com* and require a packaged linux version for ubuntu and others - i did and i am shure there will be a time this will succeed.

Have fun :guitar:

**P.S**
Normally, under linux custom program executables should be installed in */usr/**local**/share/programname* and the executable/symbolic link to it into */usr/**local**/bin/* to avoid conflict with packaged versions. But since there is no packaged version of vuescan, you can use */usr/bin* without a problems. BUT: If there will be any future versions of vuescan for linux that are packaged as a debian package, you should remember, what you once did and uninstall your custom version first ;)

---

### Post by derek_stnly1961 on 2008-05-20
I have downloaded and un-packed vuescan (ubuntu 7.10) but it wont run at all.  after double clicking "vuescan" nothing happens.  no error messages, nothing at all.   program wont start up at all.    i have checked the permissions and it is listed as an executable file.    it runs of pclinuxos with no problem at all.   any one have any ideas?

derek

---

### Post by jaywalker13 on 2008-05-28
derek_stnly1961

I just installed Hardy and had the same problem as you. From another thread in this forum I got the idea to install "libstdc++5" via Synaptic. This got Vuescan working for me. Hope it works for you.

Jay

---

### Post by richfeat on 2008-07-18
I have just installed the latest vuescan in Hardy
(in /usr/local/shared/vuescan with a link into /usr/local/bin).
Even though vuescan.bmp is there in /usr/local/shared/vuescan and is world readable, the splash screen comes up blank. It is the same if I run directly: /usr/local/shared/vuescan/vuescan
But the bmp file shows OK in nautilus.
Anyone know why?
Not a show-stopper but a bit unsettling.
I will follow the suggestion above and ask Hamrick for an Ubuntu package. So much easier to update.

---

### Post by Martje_001 on 2008-07-18
(to above poster)

Does this work in a terminal?
```
cd /usr/local/shared/vuescan
./executeable
```

---

### Post by richfeat on 2008-07-18
Yes
cd /usr/local/share/vuescan
./vuescan
works, but
cd 
/usr/local/share/vuescan/vuescan
does not.
I guess there is an easy explanation ...

---

### Post by Martje_001 on 2008-07-18
Yes there is. 'cd' takes you into a directory, so all the relative paths change. If you do **cd /usr/local/vuescan/vuescan**,you will get an error because it's not a directory.

So what you have to do, is the following:
```
sudo rm /usr/bin/vuescan
gksudo gedit /usr/bin/vuescan
```
and paste the following:
```
#!/bin/bash
cd /usr/local/vuescan
./vuescan
```
and save it. Then do:
```
sudo chmod +x /usr/bin/vuescan
```
Ready!

---

### Post by richfeat on 2008-07-18
Thanks Martj, that looks reasonable.
However I tried it (in /usr/local/bin and /usr/local/share/vuescan) and the result is the same.

/usr/local/bin/vuescan contains:
----------------------------------------
#!/bin/bash
cd /usr/local/share/vuescan
./vuescan
----------------------------------------

if this is run from the home directory, the splash screen is blank.

---

### Post by Martje_001 on 2008-07-18
If I install it this way, it all runs fine:
```
sudo apt-get install libstdc++5 libstdc++6 libstdc++6-4.2-dev

cd /tmp
wget -c http://www.hamrick.com/files/vuesca84.tgz
rm -r vuescan
mkdir vuescan
cd vuescan/
tar -xzf ../vuesca84.tgz
cd ..
sudo rm -r /usr/share/local/vuescan
sudo cp -ap vuescan /usr/share/local

sudo rm /usr/local/bin/vuescan

echo '#!/bin/bash
cd /usr/share/local/vuescan
./vuescan' > ~/.vuescan324

sudo mv ~/.vuescan324 /usr/local/bin/vuescan
sudo chmod +x /usr/local/bin/vuescan
```

---

### Post by richfeat on 2008-07-23
Thanks Martje - sorry about delay, didn't notice the forum had thrown another page!

Did you mean "/usr/share/local" in your reply, and not "/usr/local/share"?
I don't have that folder on my system.
If you meant "/usr/local/share" then that is what I already have.

Anyway, I ran your "script" with "/usr/local/share" instead of "/usr/share/local" as a check. 
If I then run "cd;vuescan" I get the same as before: the splash screen comes up blank, there is a second or two delay, then vuescan opens up.

---

