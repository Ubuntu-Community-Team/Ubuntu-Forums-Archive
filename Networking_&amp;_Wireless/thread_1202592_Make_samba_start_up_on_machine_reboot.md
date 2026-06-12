---
title: "Make samba start up on machine reboot"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by cr0wn3r on 2009-07-02
When I reboot my Ubuntu box it doesnt start up the samba shares automatically - I have to manually start samba once the machine has finished booting up.

How would I go about creating a script or something that did 
etc/init.d/samba start 
as part of the start up process?

---

### Post by Boondoklife on 2009-07-02
Try this site: [http://www.debianhelp.co.uk/initscripts.htm](http://www.debianhelp.co.uk/initscripts.htm)

---

### Post by dmizer on 2009-07-02
It should be set up to automatically start on reboot upon install. If it's not, the only thing I can think of is that it's been manually disabled in system > administration > services ... that, or there's something wrong with your smb.conf file.

---

### Post by cr0wn3r on 2009-07-05
well I've had a look, but I'm no closer to sorting it.

When I reboot the machine, samba isnt in the 
"system > administration > services" 
list.

I can't see anything in the samba conf file to indicate that it shouldnt start up on boot, and the conf file in general seems ok as all my shares are working as configured (after I start samba manually...).

Is there just a way of adding a .sh script to be run on start up, that will issue the /etc/init.d/samba start command?

I had a look at the debian link and tried the rcconf but couldnt figure it out. update-rc.d man is a little beyond me... not entirely sure how to do it with this method and don't want to break something...

Thanks guys.

---

### Post by Boondoklife on 2009-07-05
This was pulled right from the site I linked you to:
```
[FONT=Verdana][SIZE=1][SIZE=2]update-rc.d samba defaults
```[/SIZE][/SIZE][/FONT]

---

### Post by cr0wn3r on 2009-07-06
Apologies. However, it just tells me a system startup link for samba already exists. 

Odd.

---

### Post by Boondoklife on 2009-07-06
Have you tried to run the start up script manually and see if it gives you any errors?

---

### Post by cr0wn3r on 2009-07-06
Thanks for the replies.

I wasnt sure how to do what you suggested and couldnt see any clues when searching, so I made a guess and did:

sudo ./rc 2

It seems to be the start up script, although after almost every line of execution it outputs Permission Denied or Operation not permitted.

---

### Post by Boondoklife on 2009-07-06
lets try sudo /etc/init.d/samba start

---

### Post by cr0wn3r on 2009-07-06
Hey

That one works fine. What led me to post here was that I was frustrated by always having to type that command when I restart my machine, in order to get the samba filesharing back up and running.

So yeah. Thats what I've been doing to get samba started after each reboot.

---

### Post by Boondoklife on 2009-07-06
Well only thing left I can think of is to remove it from the default runlevels and then try to reinstall it into them. A long shot but really the last thing I can think of.

[FONT=Verdana][SIZE=1][SIZE=2]sudo update-rc.d -f samba remove[/SIZE][/SIZE][/FONT]

---

### Post by cr0wn3r on 2009-07-06
ok, well no luck with that one.

Thanks for your help though.

How would I add my own start up script to automate it?

I tried putting 

```
/etc/init.d/samba start
```

in to myscript.sh

And then did

```
update-rc.d myscript.sh defaults
```



Am I barking up the wrong tree? Because that doesnt seem to work either!

---

### Post by Boondoklife on 2009-07-06
You would also have to make the script executable chmod +x filename but yes it should work.

---

### Post by topcause on 2009-11-30
I have been having a similar issues with 9.10. Samba would actually start and then after a min or two would stop.  I was able to see this by downloading the Service Manager below since 9.10 version of Ubuntu does not come with it anymore.
[http://opensystems.ath.cx/gio/modules.php?name=Downloads&d_op=getit&lid=16](http://opensystems.ath.cx/gio/modules.php?name=Downloads&d_op=getit&lid=16)
 
So I strangely enough I got this fixed by stopping Samba & Winbind.  For some strange reason I'm still able to use the shared folders and Windows boxes on the network can see ping the hostname.  I have no clue if CUPS is doing the job or another processes. Unfortunately I'm still learning the Linux world....

---

### Post by munky99999 on 2009-12-07
known bug in 9.1

Not sure if there's a fix yet for it.

Other then never turn off the computer. Hey that's my fix and it's working!

---

### Post by dontgetshocked on 2009-12-10
Very Funny, Love that commercial!

---

### Post by theToolman on 2010-01-13
The samba package has finally been fixed in karmic-updates; 

[https://bugs.launchpad.net/ubuntu/karmic/+source/samba/+bug/462169](https://bugs.launchpad.net/ubuntu/karmic/+source/samba/+bug/462169)

ensure you have "karmic-updates" enabled in your /etc/init.d/sources.list , and do an apt update and upgrade.

Don't forget to remove the workaround detailed earlier if you were using it :)

---

### Post by dontgetshocked on 2010-01-13
ZI cant even find this version 3.4 and even nmbd and there is nothing in the /etc/init.d/sources.list   ! Totally confused about all of this.In package manager there is only versions 2.3.4.0 and 4.0.

---

