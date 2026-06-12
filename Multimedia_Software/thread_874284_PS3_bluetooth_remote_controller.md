---
title: "PS3 bluetooth remote controller"
date: 2008-07-29
forum: Multimedia Software
---

### Post by wild_oscar on 2008-07-29
**The Ubuntu guide for having a PS3 Bluetooth remote controler working on your computer**

**Motivation:**
To have a remote controller to control most of the multimedia functions in Xine, Amarok and the likes on my Ubuntu machine

**Prerequisites:**
- Compilation environment (TODO - don't recall which packages are necessary)
- Browser witg [http://ant.starikov.googlepages.com/linuxdriverforsonybdremote2](http://ant.starikov.googlepages.com/linuxdriverforsonybdremote2) page opened
- Package bluez-utils
- Package lirc
- A PS3 Bluetooth remote controller (DUH!)

[B]Ubuntu version tested:
[/B]Ubuntu 8.10 Hardy[B]Guide

Part I - Installation

[/B]1) The first part of the process is pretty well described in Antst's webpage: 


 First you need to get sources for BT BD Remote Daemon from [downloads page.]("http://ant.starikov.googlepages.com/downloads")
 Then you need to compile it. Just type "make" in directory with source files. You'll get binary called "bdremoted". You can copy it whenever it suits you. For example to /usr/local/sbin.
 
2) Find your remote's address. Also described on his webpage:

Now you can type in root console "hcitool scan" and then press simultaneously "Start" and "Enter" buttons on remote for about 5 seconds.
 You should see something like:
 hostname # hcitool scan                                                         
 Scanning ...                                                                    
         00:19:C1:5A:F1:3F       BD Remote Control                               
 hostname #  
 

 00:19:C1:5A:F1:3F - is the address of your remote, which you can use for configuration

3) The next step is to make the connection between your remote and your computer. this is done by starting the remote's "damon" (the driver you've just installed) and by linking it to LIRC, the well known remote controle daemon for Linux. Lirc has a special option so it can listen to communications on a specific (computer) port, and this is how it'll all be glued.

This is also where I found Ubuntu to need a special treatment. It seems that the bluetooth daemon can't be running when the bdremote and lircd commands are issued, so what you'll want is something like:
> 
sudo /etc/init.d/bluetooth stop
 sudo /usr/bin/bdremoted -p 8888 -a 00:19:C1:5A:F1:3F 
 sudo lircd -H null --connect 127.0.0.1:8888
 sudo /etc/init.d/bluetooth start


Replacing 00:19:C1:5A:F1:3F with the address you got from the previous step.

4) If all went well, the connection should have been started by now. You should run "irw", which is a little program that displays every button press you make on your remote control.
So go ahead, start irw. Press some buttons on your remote and you should see some lines on your shell like:

0004 00 num5 SonyBDRemote
0004 01 num5 SonyBDRemote
0005 00 num6 SonyBDRemote
0034 00 scanfwd SonyBDRemote

You have finished installing everything. If all went well, you should have your environment correctly configured. For troubleshooting, consult Part IV of the guide.

[B]Part II - Configuration

[/B]Now that you have your environment set up, it's time to make your remote do more than just display stuff on your shell! This is done by configuring the .lircrc file that should be located on your $HOME folder (~/.lircrc).

Your reference should be:
[http://www.lirc.org/html/configure.html#lircrc_format](http://www.lirc.org/html/configure.html#lircrc_format)
[http://www.g-loaded.eu/2006/01/10/how-to-configure-and-use-lirc/](http://www.g-loaded.eu/2006/01/10/how-to-configure-and-use-lirc/) (from "Application and Lirc support" onwards).

.lircrc is the configuration file that tells Lirc what to do when you press a button on a remote. As the second reference page says, you should learn that there are basically three types of applications:

[LIST=1]
[*]Those which could and actually have been built with LIRC support. These act as LIRC clients when there is a running LIRC daemon.
[*]Those which do support LIRC, but have not been compiled with the LIRC support enabled.
[*]Those which do not support LIRC at all.
[/LIST]
 Lets forget about number 2 (you would have to recompile them with LIRC support enabled). We are reduced to "built in LIRC support" and "no LIRC support". For the latest, we can control them using the irexec program.

First things first, lets have a look at a basic configuration entry in .lircrc:

begin
    remote = SonyBDRemote
    button = play
    prog   = xine
    config = Play
end

Almost every option is pretty self-explanatory. The "remote", well, the remote you'll use. You'll want SonyBDRemote here.
"button" is the remote button you press.
"prog" is the program you want to control
"config" is what you want that button to do

Recall when you ran "irw", you got lines like:
0005 00 num6 SonyBDRemote

The program provides the name of the remote you'll put on .lircrc and the name of the button you press (in the example, num6). When you're writing your configuration file, you may want to check in irw for the name of a particular button.

In the .lircrc entry example, I wanted to control the Xine program, which has built-in LIRC support. Therefore, LIRC knows what the "Play" config is.

For a better reference of the available options in Xine, check [http://xinehq.de/index.php/readme#2.4.4](http://xinehq.de/index.php/readme#2.4.4).


TODO - Next, I'll show you how to work with irexec. In the meantime, check the reference pages I showed you.

[B]Part III - Making it pretty

[/B]TODO - I'm developing a simple init.d script so that the remote works as soon as you start your computer.

[B]Part IV - Troubleshooting
[/B]One minor (and unconfirmed) issue I ran into was that my computer didn't shutdown when the programs were active. To fix this, I added a shutdown script (run when the computer is shutting down !!), which I'll update on Part III of the guide.TODO - tell me what doesn't work.

---

### Post by yojimba on 2008-08-01
Bump . . . 

Hope you can get it worked out and can get a guide posted. I'm a newb looking to do the same thing.

---

### Post by wild_oscar on 2008-08-02
Guide created. Please read and tell me if you were able to work it out!

---

### Post by yojimba on 2008-08-09
Are you using the remote with a PS3 as well?

---

### Post by wild_oscar on 2008-08-11
> **yojimba said:**
> Are you using the remote with a PS3 as well?

Not yet, as I'm lacking an important piece of hardware for that - the PS3.
Will buy one as soon as someone brings me one from the USA (where it's half the price with the current euro-dollar rates)!

---

### Post by wild_oscar on 2008-09-11
> **yojimba said:**
> Are you using the remote with a PS3 as well?

Actually, I now got a PS3 and my bdremoted stopped working. Don't know if the two are related!

---

### Post by hedgehog.at on 2008-10-07
i think that the remote can only be coupled with one device at one time. so when you connect it to your ps3 it's loosing the "settings" for the connection to your ubuntu box. does it still not work when you try to do your described process from the beginning (including finding out the hardware address ...), maybe the remote switches to the coupling mode when you press the 2 buttons mentioned in your article together.

---

### Post by wild_oscar on 2008-10-07
> **hedgehog.at said:**
> i think that the remote can only be coupled with one device at one time. so when you connect it to your ps3 it's loosing the "settings" for the connection to your ubuntu box. does it still not work when you try to do your described process from the beginning (including finding out the hardware address ...), maybe the remote switches to the coupling mode when you press the 2 buttons mentioned in your article together.


You are correct. 

I managed to make it work again by coupling it again to my pc, using Brett's python script found here: [http://ps3mods.blogspot.com/2007/03/bd-remote-for-linux-update.html]("http://ps3mods.blogspot.com/2007/03/bd-remote-for-linux-update.html")

---

### Post by hedgehog.at on 2008-10-07
thanks for the link ... sounds great, i'm going to test the whole procedure today in the evening

---

### Post by atleberg on 2008-11-07
I'm on 8.10 and can't get the driver to work. I have no problem getting the controller-id and starting the script, but irw shows no output at all.

I've also tried to telnet into port 8888, but nothing shows up there either. Increasing debug level when launching driver doesn't seem to output anything more in stdout, dmesg or /var/log/messages when I do keypresses.

At the momen't I'm kind of stuck so any input of how to proceed is appreciated :)

---

### Post by wild_oscar on 2008-11-07
> **atleberg said:**
> I'm on 8.10 and can't get the driver to work. I have no problem getting the controller-id and starting the script, but irw shows no output at all.

I've also tried to telnet into port 8888, but nothing shows up there either. Increasing debug level when launching driver doesn't seem to output anything more in stdout, dmesg or /var/log/messages when I do keypresses.

At the momen't I'm kind of stuck so any input of how to proceed is appreciated :)


1) Have you used the remote on the ps3?
2) Have you tried Brett's python script?

---

### Post by atleberg on 2008-11-07
Since I haven't baught myselfe a PS3 yet the answer to the first question is no ;)

I'm going to test out the python script tonight so let's hope that works :)

-atle

---

### Post by Wolfspirit on 2008-11-08
Any update on this?  I also get the same behavior in 8.10.  The bdremoted daemon loads and lircd connects to it just fine but irw shows nothing.  I even recompiled bdremoted for the new kernel thinking that was it and nothing.

---

### Post by atleberg on 2008-11-09
Since I'm using my remote exclusively for XBMC I ended up solving this with "ps3_remote.py" and the event-server that's included in XBMC. Now I don't have to worry about Lirc and relevant drivers at all :)

---

### Post by Wolfspirit on 2008-11-09
Can you tell me how that works?  I set up the cakemote script and it works but how do I transfer that to other programs such as mythtv etc. ?

---

### Post by atleberg on 2008-11-10
I have no experience using the cakemote script so I don't think I can be helpful there.

If you are interrested in running the remote with XBMC you can have a look at [http://xbmc.org/wiki/?title=EventServer]("http://xbmc.org/wiki/?title=EventServer") for a howto. I'm not sure if this script can be transferred to work for other application, but I have my doubts since it's written explicitly for XBMC.

atle

---

### Post by Wolfspirit on 2008-11-11
For anyone else who is interested in getting the PS3 BD Remote working under ubuntu 8.10, I was able to do this using the cakemote.py script from [http://www2.apebox.org/wordpress/programming/28/]("http://www2.apebox.org/wordpress/programming/28/")  To start the remote upon reboot, just make an init script or place the following in the /etc/rc.local file:

sudo modprobe uinput
sudo /etc/init.d/cakemote.py &

The cakemote.py script should be downloaded from the link above.  You will have to hit the start and enter buttons together and hold them down before kicking this off and I believe this will have to be done after every reboot.  The bdremoted daemon used to work with 8.04 and would integrate with lirc but no longer seems to work with 8.10 so this is an alternative.  This literally maps every button on the PS3 remote with a keyboard press instead of lirc so you will have to configure mythtv and your other applications around that basis.

---

### Post by dogshu on 2009-01-16
For those having problems getting the device to permanently pair with your computer:  according to this bluez mailing list post:
[http://marc.info/?l=linux-bluetooth&m=123205242411328&w=2](http://marc.info/?l=linux-bluetooth&m=123205242411328&w=2)

You can use bluez-gnome to permanently pair the device with your computer.

---

### Post by Bigm8 on 2009-01-21
I am currently using the ps3 remote for a mythtv frontend with ubuntu 9.04.
The machine stays on all the time. I had many difficulties getting the remote to work. It would never pair and work like it should, until I found out that the bluetooth daemon interferes with the operation of bdremote. I am using the bdremote that feeds to lirc.
For me /etc/init.d/bluetooth has to be started and then stopped before bdremote and lirc start. When I reboot the machine (which is very rarely), I stop the /etc/init.d/bluetooth service and then restart /etc/init.d/bdremote and /etc/init.d/lirc. 

This is not perfect, but it is well enough for me. If someone wants to take this information to make a more automatic setup it would be great.

---

### Post by tzoom84 on 2009-02-01
So just to verify, a PS3 can only be bluetooth-paired to a single device at any given time? 

I am interested in using it on my linux machine, but use the controllers a lot for my PS3. So if only a single pairing is allowed, I may just stick with the USB cable connection.

Thanks.

---

### Post by BiggerGeek on 2009-02-26
So I finally go my remote working through lirc, but now it doesn't stay connected if I'm not using it.

I just got it working last night, and come morning it doesn't work. I have to go through the process of stopping everything,
use the cakemote script first (for some reason), start bdremoted, start lircd, and then start bluetooth, and it works again. But it is useless if I have to do this every time.

Do you guys have hidd enabled? The mythtv guide says turn it off, but another guide for ps3 remote with amarok [(here)]("http://ubuntuforums.org/showthread.php?t=1031070") says turn it on. I guess I will try it with hidd one when I get home.

---

### Post by wild_oscar on 2009-02-26
> **BiggerGeek said:**
> So I finally go my remote working through lirc, but now it doesn't stay connected if I'm not using it.

I just got it working last night, and come morning it doesn't work. I have to go through the process of stopping everything,
use the cakemote script first (for some reason), start bdremoted, start lircd, and then start bluetooth, and it works again. But it is useless if I have to do this every time.

Do you guys have hidd enabled? The mythtv guide says turn it off, but another guide for ps3 remote with amarok [(here)]("http://ubuntuforums.org/showthread.php?t=1031070") says turn it on. I guess I will try it with hidd one when I get home.

Have you registered the remote with another device (eg: PS3) in between? You'll have to re-register it with cakemote if you do.

---

### Post by sony_gamer on 2009-02-28
when i ran make in the bdremote-0.2 folder i get this response

```
brock@brock-laptop:~/programs/bdremote-0.2$ make
gcc -O3 bdremoted.c -o bdremoted -lpthread
bdremoted.c:39:33: error: bluetooth/bluetooth.h: No such file or directory
bdremoted.c:40:27: error: bluetooth/hci.h: No such file or directory
bdremoted.c:41:31: error: bluetooth/hci_lib.h: No such file or directory
bdremoted.c:42:29: error: bluetooth/l2cap.h: No such file or directory
bdremoted.c:43:27: error: bluetooth/sdp.h: No such file or directory
bdremoted.c:44:28: error: bluetooth/hidp.h: No such file or directory
bdremoted.c: In function ‘main’:
bdremoted.c:138: warning: ignoring return value of ‘nice’, declared with attribute warn_unused_result
bdremoted.c: At top level:
bdremoted.c:265: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
bdremoted.c:302: error: expected declaration specifiers or ‘...’ before ‘bdaddr_t’
bdremoted.c: In function ‘l2cap_accept’:
bdremoted.c:304: error: storage size of ‘addr’ isn’t known
bdremoted.c:314: error: ‘bdaddr’ undeclared (first use in this function)
bdremoted.c:314: error: (Each undeclared identifier is reported only once
bdremoted.c:314: error: for each function it appears in.)
bdremoted.c: In function ‘btbd_check’:
bdremoted.c:321: error: storage size of ‘addr’ isn’t known
bdremoted.c: In function ‘btbd_wait_connection’:
bdremoted.c:343: error: ‘bdaddr_t’ undeclared (first use in this function)
bdremoted.c:343: error: expected ‘;’ before ‘bdaddr’
bdremoted.c:352: error: ‘bdaddr’ undeclared (first use in this function)
bdremoted.c:352: error: ‘BDADDR_ANY’ undeclared (first use in this function)
bdremoted.c:354: error: ‘BTPROTO_HIDP’ undeclared (first use in this function)
bdremoted.c:400: error: too many arguments to function ‘l2cap_accept’
bdremoted.c:401: error: too many arguments to function ‘l2cap_accept’
make: *** [all] Error 1
```

Can anyone tell me what I'm doing that's wrong?

---

### Post by BiggerGeek on 2009-03-08
> **wild_oscar said:**
> Have you registered the remote with another device (eg: PS3) in between? You'll have to re-register it with cakemote if you do.

nope. In fact, the playstation was powered down the whole time.

---

### Post by Neo_The_User on 2009-03-08
[https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)

Cheers!

---

### Post by lift28 on 2009-04-03
I could not get this to work either.
so i tweak cakemote.py for my setup- works great, but only 4-5 days of battery life.
here is link to cakemote.py tweak for mythtv
[http://www.mythtv.org/wiki/PS3_Remote]("http://www.mythtv.org/wiki/PS3_Remote")

---

### Post by potats on 2009-04-15
any chance you can re-post the cakemote-mythtv.py  ? Both links are down.  help plz!!!!!!!!

thanks

---

### Post by lift28 on 2009-05-02
i fixed.
sorry for the poor choice of host.

---

### Post by balderson on 2009-05-05
> **sony_gamer said:**
> when i ran make in the bdremote-0.2 folder i get this response

```
brock@brock-laptop:~/programs/bdremote-0.2$ make
gcc -O3 bdremoted.c -o bdremoted -lpthread
bdremoted.c:39:33: error: bluetooth/bluetooth.h: No such file or directory
bdremoted.c:40:27: error: bluetooth/hci.h: No such file or directory
bdremoted.c:41:31: error: bluetooth/hci_lib.h: No such file or directory
bdremoted.c:42:29: error: bluetooth/l2cap.h: No such file or directory
bdremoted.c:43:27: error: bluetooth/sdp.h: No such file or directory
bdremoted.c:44:28: error: bluetooth/hidp.h: No such file or directory
bdremoted.c: In function ‘main’:
bdremoted.c:138: warning: ignoring return value of ‘nice’, declared with attribute warn_unused_result
bdremoted.c: At top level:
bdremoted.c:265: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
bdremoted.c:302: error: expected declaration specifiers or ‘...’ before ‘bdaddr_t’
bdremoted.c: In function ‘l2cap_accept’:
bdremoted.c:304: error: storage size of ‘addr’ isn’t known
bdremoted.c:314: error: ‘bdaddr’ undeclared (first use in this function)
bdremoted.c:314: error: (Each undeclared identifier is reported only once
bdremoted.c:314: error: for each function it appears in.)
bdremoted.c: In function ‘btbd_check’:
bdremoted.c:321: error: storage size of ‘addr’ isn’t known
bdremoted.c: In function ‘btbd_wait_connection’:
bdremoted.c:343: error: ‘bdaddr_t’ undeclared (first use in this function)
bdremoted.c:343: error: expected ‘;’ before ‘bdaddr’
bdremoted.c:352: error: ‘bdaddr’ undeclared (first use in this function)
bdremoted.c:352: error: ‘BDADDR_ANY’ undeclared (first use in this function)
bdremoted.c:354: error: ‘BTPROTO_HIDP’ undeclared (first use in this function)
bdremoted.c:400: error: too many arguments to function ‘l2cap_accept’
bdremoted.c:401: error: too many arguments to function ‘l2cap_accept’
make: *** [all] Error 1
```

Can anyone tell me what I'm doing that's wrong?

I got this too.

Does this not work with 9.04? Is there anything we can do to get the remote working?

---

### Post by wipmonkey on 2009-05-12
> **balderson said:**
> I got this too.

Does this not work with 9.04? Is there anything we can do to get the remote working?

I'm using 9.04 and it compiled fine for me.. make sure you have **libbluetooth-dev** installed.

---

### Post by wild_oscar on 2009-05-13
Also, on a long shot - make sure you don't have any white spaces in the path. (like /home/user/my remote stuff/bdremoted). Sometimes programmers forget that and the compiler fails to find the correct files.

---

### Post by Eldis on 2009-08-28
I've followed this guide now on two different computers and I didn't get it to work on either.

So compiling works fine, hci scan finds the device.

I've stopped bluetooth and lirc before starting up.

sudo /usr/local/bin/bdremoted -a 00:23:06:E9:E8:34 -d 5 -p 8888
sudo lircd -H null --connect 127.0.0.1:8888

but no output on irw.

Any way to debug this ? I'm not afraid of a bit of work to get this up and running just need some help so I can start debugging.

---

### Post by zaphod777 on 2009-12-14
can anyone point me in the direction I might want to go to right a program to emulate a ps3 remote to have Linux remote control the PS3 XMB.

I then want to write an app for android.

---

### Post by wipmonkey on 2009-12-22
> **zaphod777 said:**
> can anyone point me in the direction I might want to go to right a program to emulate a ps3 remote to have Linux remote control the PS3 XMB.

I then want to write an app for android.

To simulate lirc button presses you can use [irsend]("http://www.lirc.org/html/irsend.html") its a part of lirc. You have to run lircd with -a --allow-simulate.

---

### Post by sparkix on 2010-03-12
I got it to work on Karmic (9.10) server.  By it, I mean bdremote-ng (an offshoot of bdremote).  I don't know the difference other than I managed to get it working first (I was trying both in parallel).

[http://code.google.com/p/bdremote-ng/wiki/README](http://code.google.com/p/bdremote-ng/wiki/README)

The following commands (using the correct address) in sequence allow irw to see the remote output.

/etc/init.d/bluetooth stop
bdremoteng -a 00:11:22:33:44:55
lircd -H null --connect 127.0.0.1:8888
/etc/init.d/bluetooth start

I did find that the -d flag (debug) for bdremoteng caused it to not work.  Once I removed that, it worked fine.  For some reason, the debug setting causes it to not work.

---

