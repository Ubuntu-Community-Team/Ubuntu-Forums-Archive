---
title: "Message: All tuners are currently occupied"
date: 2014-01-17
forum: Mythbuntu
---

### Post by daniele4 on 2014-01-17
Ho citato il problema nella discussione [http://forum.ubuntu-it.org/viewtopic.php?f=73&t=572400](http://forum.ubuntu-it.org/viewtopic.php?f=73&t=572400)

[COLOR=#101010][FONT=Ubuntu]Avviando [/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu]**Guardare la TV**[/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu] compare il messaggio [/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]**Impossibile connettere al backed server primario. E in esecuzione ? L'indirizzo IP è impostato.**[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]e successivamente [/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu]**Tutti i sintonizzatori sono attualmente occupati**[/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu].

Aiuto ![/FONT][/COLOR]

---

### Post by QIII on 2014-01-17
Hello!

This is an English language forum.  While some here may speak Italian, we expect that all threads will be carried out in English.

We do welcome those who do not speak English well and will try to accommodate, of course.

---

### Post by daniele4 on 2014-01-17
I started "Watch TV" and the following message appears: 
"Unable to connect to the primary server backed. And running &#8226; The IP address is set." 
and immediately afterwards: "All tuners are currently occupied." 


Although in English, I need a help ] (*,)

---

### Post by QIII on 2014-01-17
You are more likely to get help in English.  :)

Could you also translate your title?   In your first post, go to Edit -> Go Advanced.

I just want to be sure you get help rather than being ignored.

---

### Post by tuat2 on 2014-01-18
Ok, first check if the backend is running. On a terminal, you may want to check "ps aux | grep backend" to check if mythbackend is running.

Also check the folder "/dev/dvb/", if it has any DVB devices.

Did it ever work or is it a new installation?
What did you do before it stopped working?

---

### Post by daniele4 on 2014-01-20
Ciao** [COLOR=#000000][tuat2]("http://ubuntuforums.org/member.php?u=1892202") [/COLOR]**:P
Thank you for having responded !!!
I try to write with Google translator ;).

I summarize with some screenshots
for a better visual for all languages.

When I open **MythTV Frontend** 
and: Guardare la TV (**Watching tv)**
The first error message is: ([FONT=arial]Unable to connect to the primary server backed. And running &#8226; The IP address is set.[/FONT])
[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/mythtv/Mythtv%20Fronted_%20Impossibile%20collegare%20al%20backed.jpeg[/IMG]

The second error message is: ([FONT=arial]All tuners are currently occupied[/FONT])
[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/mythtv/Mythtv%20Fronted_%20collegati%20pi%C3%B9%20sintonizzatori.jpeg[/IMG]

Now try your suggestions....

---

### Post by daniele4 on 2014-01-20
1) *with the terminal command: **ps aux | grep backend***

```
danmyth@danmyth-EP41T-UD3L:~$ ps aux | grep backendmythtv    1505  0.6  1.3 1540684 55132 ?       Sl   11:17   0:41 /usr/bin/mythbackend --syslog local7 --user mythtv
danmyth   3208  0.0  0.0   9424   932 pts/2    S+   13:09   0:00 grep --color=auto backend

```

2) [COLOR=#000000]*Also check the folder "/dev/dvb/", if it has any DVB devices.*
[/COLOR]```
danmyth@danmyth-EP41T-UD3L:/dev/dvb/adapter0$ ls[COLOR=#000000]
[/COLOR]
demux0  dvr0  frontend0  net0
```
[COLOR=#000000]
3) [/COLOR][COLOR=#000000]*Did it ever work or is it a new installation?*
[/COLOR]It gave me the same error message, and then I was able to operate the TV

It worked after making the connection from the: 5. Connessioni di ingresso (**Connections menu input)**
[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/mythtv/Mythtv_5%20Connessioni%20di%20ingresso.jpeg[/IMG]

to the entry: Collegare la sorgente per l'ingresso (**Connect the source for input**) 
- I chose to Video source: "Terratec" (name given previously when I set the Source)
[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/mythtv/Mythtv_5%201%20Collegare%20la%20sorgente%20per%20ingresso.jpeg[/IMG]
And after work!

4) [I][COLOR=#000000]What did you do before it stopped working?
[/COLOR][/I]Perhaps the change is wrong to have erased the number of IP by default.
in: 1. Generale (**General**) 
[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/mythtv/Mythtv%20Bakend%20_1%20Generale.jpeg[/IMG]

and: Indirizzo host impostazioni backend (**host address settings backend)**
[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/mythtv/Mythtv%20Baked_1_2%20indirizz%20host.jpeg[/IMG]

I do not remember the number of the default IP

My connection type is automatic without an address:
[IMG]https://dl.dropboxusercontent.com/u/46733398/ubuntu%20forum/mythtv/connessione%20internet.jpeg[/IMG]

What an effort ... 
I could not explain it any better than that
from a Sicilian !

I'm struggling on several fronts,
Although maybe off topic,
I also tried to install **MythTV**
with :
- Ubuntu Software Center
- At many sites , including the official one, ( with compiler errors )
**Ubuntu 13.10** but to no avail.


1 ) Been running an updated guide ?
2 ) MythTV is compatible with Ubuntu 13:10
or you have to wait ?

help!
] (*,)

---

### Post by tuat2 on 2014-01-20
Thanks for the screenshots.

The DVB adapter doesn't seem to be the problem, because the backend seems to recognize your /dev/dvb/adapter0... And the other screenshots look OK as well.

But you set the network to DHCP. Are you sure your MythTV-Box actually has the IP 192.168.1.33? Maybe you should use a static network setup!

You can check the actual IP address of your box by typing "ifconfig" in the terminal and check the "inet addr" value it prints out.

---

### Post by daniele4 on 2014-01-21
!!! Solved !!! 
Great [SIZE=4]**tuat2**[/SIZE] ! : P
It was enough to put the exact address from the terminal command " ifconfig" that you suggested to me !
Now reinstall all over again, the iso Mythbuntu clean and stable
I have changed too much and that has problems in the management of application windows (terminal, Cromium ... ) and mouse .


Speaking of the mouse, you know how to make visible his cursor over the menu " MythTV Frontend " and " MythTV Backend Setup" ?
I did not succeed .


One last thing .
Do you know if MythTV is compatible with the new Ubuntu 13:10
and a good guide or forum and suitable professional ?

I tried the site Ufficial : [http://ufficialehttp://www.mythtv.org/wiki/User_Manual:Initial_Installation](http://ufficialehttp://www.mythtv.org/wiki/User_Manual:Initial_Installation)

and also this MythTV Ubuntu Installation Guide: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
But I have had problems in both the compilation steps,
perhaps because they are not yet fully tested with the new and shrill 13:10 Ubuntu ? ! ?

---

### Post by tuat2 on 2014-01-21
Hi!

But even after reinstall, you should consider using a static IP address instead of DHCP!

For the mouse, there is a checkbox in the appearance menu. I believe it's Configuration -> Appearance on the first dialog. Can't verify this right now, because I am not at home. :)

MythTV should work on 13.10. For an easy installation, I recomment to use MythBuntu (which is actually based on 12.x), or you install 13.10 and use MythTV-Control-Centre (there is a package for it) to install MythTV, which also allows you to choose the version of MythTV to install. I recommend 0.27. I don't recommend using Ubuntu if it's a pure MythTV box, because the window manager "Unity" eats a lot of resources. You may want to try XUbuntu, which uses (I believe) XFCE as its window manager.
I am not using 13.x, yet, because the driver for my PayTV card adapter doesn't seem to be ready for the newer kernel versions used in 13.x.

---

### Post by daniele4 on 2014-01-21
Can I put "solved" 
and how? 

I'm sorry but I only mention for fear of the wrong forum:

Here I am trying to install on Ubuntu 13:10
[http://forum.ubuntu-it.org/viewtopic.php?f=73&t=572400&p=4520443#p4520443](http://forum.ubuntu-it.org/viewtopic.php?f=73&t=572400&p=4520443#p4520443)
which can be automatically translated using convenient Chromium or Chrome. 


I stopped at the problem, 
[http://forum.ubuntu-it.org/viewtopic.php?f=73&t=572400&p=4520443#p4520444](http://forum.ubuntu-it.org/viewtopic.php?f=73&t=572400&p=4520443#p4520444)
after the command "**sudo make install**" 
and I can not find the program "**mythbackend**" or "**mythfrontend**" to run in the path "**/usr/bin**"! 


Let's hope so!


: P

---

### Post by Iowan on 2014-01-21
> **daniele4 said:**
> Can I put "solved" 
and how? 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by tuat2 on 2014-01-22
Sorry, can't help you with issues related to compiling. I am usually using the binary packages.

---

### Post by daniele4 on 2014-01-23
Hello, my tuat2 solver! 
Where can I get this kind of problem (forum. .. or whatever)? 
What are binary packages and where can I find them?

---

### Post by tuat2 on 2014-01-23
Well, for the binary packages, you can try to install the package mythtv-control-centre. It will create an entry in the applications -> system folder. From there, you can choose the version of MythTV to install, as well as whether you want to have a frontend or combined front-/backend, etc..

Normally, the package should be available right away. If it isn't, check this page: [http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu)

---

### Post by daniele4 on 2014-01-23
Thanks as always tuat2! 
As soon as I'm home I try. 


In the meantime I opened a new discussion apart 
to distinguish **MythTVbuntu** [solved] by [MythTV in Ubuntu 13.10]("http://ubuntuforums.org/showthread.php?t=2201109") [which is definitely solve]! 


If that's okay 
I move the discussion there. 


A soon, hello!

---

