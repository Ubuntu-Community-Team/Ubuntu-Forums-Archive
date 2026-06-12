---
title: "MYTHTV INSTALL: try this if you get the dreaded database error"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by majoridiot on 2007-02-16
i'm putting together a new incarnation of my backend box and did a fresh install following our
great wikis... to see what the problem seems to be.

[I][B]i now humbly apologize to those i dismissed so easily for getting the dreaded database error when 
running mythtv-setup[/B][/I]- because i got it too.

yup, the package is slightly broken.  but GOOD NEWS! the fix seems simple.

it looks like the scripts (or whatever) that set up the PAM, borks the mythv user setup.  to fix it,
log in as your regular admin user (or anyone with sudo ability), open a terminal and:

```
# sudo passwd mythtv
```

it will prompt twice for the new password.  i used the default "mythtv".

now, log out and back in as user:mythtv pass: mythtv and run mythtv-setup.  if your results 
are like mine, all is well in the garden and you can carry on.

note that the wiki instruction that adding yourself to the mythtv group to run setup does **not**
seem work as intended at this time, so you should run mythtv-setup as user mythtv only.

i'm making mario aware immediately so that this can be remedied soonest.

:D

**EDIT**: for a hopefully definitive fix, check mario's post later in the thread:
[http://ubuntuforums.org/showpost.php?p=2166105&postcount=14](http://ubuntuforums.org/showpost.php?p=2166105&postcount=14)

---

### Post by Erlander on 2007-02-16
I fixed the database error by changing the Mysql password to the random one thrown up by Myth in the setup stage.

However I'm getting an IP address error and will have to sort out my network settings.  See first attachment below.  I'll turn off the DHCP server in my router and give all the pc's a fixed address.

My second problem is that I altered the folder where the Myth files are stored and where captured tv is kept.  Now I get the error in the second attachment.  I have been looking a hidden files and folders but can't see anything that looks relevant.  Can anyone give me the full path I should be looking at.  I have enabled sharing on /home/myth/

Rob

---

### Post by majoridiot on 2007-02-16
on the last install it generated the random pw and everything worked fine.  this time, it didn't- 
instead it came up with both user and pw as "mythtv" and wouldn't open the db.  hence, the
change.

you can determine the ip of your machine by:

```
ifconfig
```

the videos are store in /var/lib by default.  i believe this installation defaulted to /var/lib/mythtv
before i changed it.

---

### Post by Erlander on 2007-02-16
By changing to /home/mythtv I was trying to get the videos into my /home folder because it is in a larger partition than the root as per the guide.

Rob

---

### Post by majoridiot on 2007-02-16
right... that's fine.  i did the same.

that screenshot looks like you might have mistyped it.  try running mythtv-setup again and
try re-entering the directory.

---

### Post by Erlander on 2007-02-16
I've just looked at the guide again and I see that it has the larger partition mounted as /var/lib

I think I've made a big enough mess to do a re-install of Edgy and to start again.

hopefully I'll do better this time.  in the meantime I'll keep your tip on the database error in mind.  I might need it.

Rob

---

### Post by majoridiot on 2007-02-16
if your home directory is the largest partition, there's no reason you can't use it.  all you need
to do is make sure it (and all contents) are owned by mythtv:

```
sudo chown mythtv:mythtv /home/mythtv/video
```

or whatever dir you want, and then enter that into the video location in mythtv-setup.

---

### Post by Erlander on 2007-02-16
Fine.

I will try that.

Rob

---

### Post by Erlander on 2007-02-16
Still getting the IP address error and the Unable to write one too.

Will do the fresh install and get back to you.

Rob

---

### Post by Erlander on 2007-02-16
Success!!!!!!!!!!!!!

its now working with good quality sound and video.  It shouldn't be this good with my display card.

Under Win XP SP2 I'm sure it wouldn't have been this good with this setup hence the fact my XP machine has a 9700 Pro.

I had to login as the user mythtv to get the setup working for both backend and frontend.  On the frontend setup I saw the randomly generated passsword and so when I logged in as myself I was able to enter it and have it working under my normal login.

No database error.  As user mythtv I deleted the password as I had left it blank in the mysql setup.

Thank you for your encouragement.

Rob

---

### Post by williammanda on 2007-02-16
Erlander
What install guide were you using?
Thanks

---

### Post by majoridiot on 2007-02-16
glad you got it working! :D

i'll pass along the additional password info to mario.  it might help track down the install snafu.

---

### Post by majoridiot on 2007-02-16
> **williammanda said:**
> Erlander
What install guide were you using?
Thanks

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by superm1 on 2007-02-16
Okay guys - i'm pretty sure that I've tracked down the password trouble everyone is running into.  

I've updated the guide to reflect this and already told major about it.

So here is an explanation of what goes on: if you aren't in the mythtv group, you don't have permissions to read /etc/mythtv/mysql.txt.

Anytime you try to launch mythtv-setup, mythfrontend, mythbackend, or anything that connects to the database, it tries to read these files (in this order):
```
~/.mythtv/mysql.txt
/usr/share/mythtv/mysql.txt (which is a symlink to /etc/mythtv/mysql.txt)

```

The first time you launch one of those apps it checks to see if you have ~/.mythtv/mysql.txt.  If you don't, then it moves on to the next path.  If it can't read it, it moves to the next one (there are a few other defined paths that it looks, but they are irrelevant).  Now if it connects using one of those defined mysql.txt's, it doesn't save anything to ~/.mythtv.

However, if it *can't* connect to the database, it will copy /usr/share/mythtv/mysql.txt.dist to ~/.mythtv.  Now this becomes the first one that is checked **every** time, and of course its not going to have the correct password since its just the default 'mythtv' password in it.

Now the solution to the problem is this:
1) Anyone you want to have access to mythtv needs to be put into the mythtv group.  You can do this by:
```
sudo usermod -a -G mythtv USERNAME
```2) If you are logged into that user that you just added, logout and back in.
3) Remove the mysql.txt that was generated in your home directory
```
rm -rf ~/.mythtv/mysql.txt
```
4) Make sure that you can read /etc/mythtv/mysql.txt and haven't changed passwords as an alternative solution.  If you have, you will need to update /etc/mythtv/mysql.txt to match your new password.

Hopefully this should solve everyones password woes! :)

---

### Post by majoridiot on 2007-02-16
great work mario! :D

hopefully this will get more mythboxes up and running with few problems!

---

### Post by Erlander on 2007-02-16
> **williammanda said:**
> Erlander
What install guide were you using?
Thanks
williammandra,

I used the official Edgy Guide for Frontend, Backend, Desktop.  I left the mysql password blank and deleted the password "mythtv" thrown up in the backend setup.  I now feel I should have left it there as when I did the frontend setup there was a random password.

However to run mythtv-setup I gave the mythtv user a password and logged in as mythtv.

When I later tried to run the frontend from my user name I had to use the random password to get in.

I'm now noticing a very little bit of stuttering on HD channels but expect a better display card will fix that.  I don't have access to an online EPG so that is causing some problems.

Channel changing, volume and mute are working with the remote that came with the tuner but other functions are not.

Now I need to read up on lirc.

Thank you Mario for the guide.

Rob

---

### Post by superm1 on 2007-02-17
> **Erlander said:**
> williammandra,

I used the official Edgy Guide for Frontend, Backend, Desktop.  I left the mysql password blank and deleted the password "mythtv" thrown up in the backend setup.  I now feel I should have left it there as when I did the frontend setup there was a random password.

However to run mythtv-setup I gave the mythtv user a password and logged in as mythtv.

When I later tried to run the frontend from my user name I had to use the random password to get in.

I'm now noticing a very little bit of stuttering on HD channels but expect a better display card will fix that.  I don't have access to an online EPG so that is causing some problems.

Channel changing, volume and mute are working with the remote that came with the tuner but other functions are not.

Now I need to read up on lirc.

Thank you Mario for the guide.

Rob
Rob, glad things are starting to work out much better for you.  Once you get a decent nvidia card - you can setup xvmc and get much better luck with the stuttering from HD channels.  It's quite a blessing.

---

### Post by majoridiot on 2007-02-17
> **superm1 said:**
> Rob, glad things are starting to work out much better for you.  Once you get a decent nvidia card - you can setup xvmc and get much better luck with the stuttering from HD channels.  It's quite a blessing.

now that i've beefeed my backend up to an amd64 with more HD and ram, i'm going to take a
run at xvmc and see how well HD will run on my frontend, whilst i do all the other things i do
at the same time.

from what i've read, it looks like it could work very well on this 3 head desktop/frontend.

---

### Post by Erlander on 2007-02-18
> **superm1 said:**
> Rob, glad things are starting to work out much better for you.  Once you get a decent nvidia card - you can setup xvmc and get much better luck with the stuttering from HD channels.  It's quite a blessing.

Yes,  I'm planning on getting a Gigabyte 7600GS seen here:  [http://tw.giga-byte.com/Products/VGA/Products_Overview.aspx?ProductID=2334](http://tw.giga-byte.com/Products/VGA/Products_Overview.aspx?ProductID=2334)

Based on the way that I've had HDTV running on the ATI 9700 Pro on my XP nmachine it should be OK.

Major,  (Sorry but I can't use your whole login as that clearly is'nt true) Also based on how that pc went you should have no difficulty.  I used to watch tv on one monitor and do other things on the other.  Its also an AMD Athlon 3200+

Rob

---

### Post by majoridiot on 2007-02-18
> **Erlander said:**
> I used to watch tv on one monitor and do other things on the other.  Its also an AMD Athlon 3200+

Rob

my third screen is 80% tv/movie only use (and background noise ;)), and i notice that it will
lag and flicker if i do heavy screen axx to heads one or two... like scrolling a LOT of text 
or major 3d accel.

i think it's more due to the way X11 currently (and incorrectly) implements multiple-head, 
multiple-desktop setups, than the nvidia drivers.  there's more than enough GPU and ram to
handle things like this, but it does stumble.

so the first test of xvmc is obviously whether or not it improves my typical setup/usage, then
we'll try some hdtv.

---

### Post by SirShaggy on 2007-02-18
Wow, maybe it's just too late for me, but, I am having issues and got lost! I installed my Hauppauge PVR-150 into the PCI slot, fired up Kubuntu and then installed the IVTV Driver.

shaggy@shaggy-desktop:~$ dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac
[17183370.592000] ivtv:  ==================== START INIT IVTV ====================
[17183370.592000] ivtv:  version 0.7.0 (tagged release) loading
[17183370.592000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17183370.592000] ivtv:  In case of problems please include the debug info between
[17183370.592000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17183370.592000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17183370.592000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17183370.592000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[17183370.592000] ACPI: PCI Interrupt 0000:05:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 233
[17183370.592000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17183370.636000] tveeprom 3-0050: Hauppauge model 26552, rev F0A3, serial# 10171827
[17183370.636000] tveeprom 3-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[17183370.636000] tveeprom 3-0050: TV standards NTSC(M) (eeprom 0x08)
[17183370.636000] tveeprom 3-0050: audio processor is CX25843 (idx 37)
[17183370.636000] tveeprom 3-0050: decoder processor is CX25843 (idx 30)
[17183370.636000] tveeprom 3-0050: has radio, has no IR remote
[17183370.696000] tuner 3-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17183370.868000] tda9887 3-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17183370.888000] cx25840 3-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17183374.460000] cx25840 3-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[17183374.536000] wm8775 3-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17183375.212000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17183375.428000] ivtv0: Encoder revision: 0x02050032
[17183375.428000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17183375.428000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17183375.428000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17183375.428000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17183375.432000] ivtv0: Create encoder radio stream
[17183375.432000] tuner 3-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[17183375.556000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[17183375.556000] ivtv:  ====================  END INIT IVTV  ====================
shaggy@shaggy-desktop:~$ 


I saw no errors, so I went to [https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Frontend_Desktop) for a combined frontend/desktop setup. I followed the instructions to the end. I installed mythplugins before I read: "For a non-backend machine, the only un-applicable plugin is mythweb. Don't install the mythplugins metapackage. This will cause all the plugins including mythweb to be installed."
I figure I can just remove mythweb, Right?

Anyway, I logged out of the current session and logged back in as myself again. I opened a terminal and typed mythtv-setup. This is where I saw it fall apart. 

All those options and no idea what to type or where....I knew to use NTSC and that's it. Is there a place to look that shows me what options I am to select or what to type? Thanks for your time,
SirShaggy

---

### Post by SirShaggy on 2007-02-18
I forgot to say, during the setup I changed nothing and just left all of the defaults that were in the blanks. I just closed it at that point because I wasn't sure.
I pland to use and antenna to receive all tv and fm stations, so broadcast?
System:
ASUS M2NBP-VM CSM motherboard
AMD Athlon X2 5200+ @2808GHz
Zalman CNPS9500 HSF
Corsair TWIN2X2048-C6400C4D memory
Soundblaster Audigy 2SE
Hauppauge WinTV PVR-150 Tuner Card
XFX PVT73GUGD3 Geforce 7600GT XXX graphics card
Belkin F5U602 PCI-E x1 1394b/USB card
Seagate 7200.9 IDE 120GB Hard Drive and
(2) Seagate 7200.10 SATA II 200GB Hard Drives.

I figure this should be fine for some tv viewing/recording.

---

### Post by Erlander on 2007-02-18
Sorry Sir,

I fear I won't be much use to you as one of my problems was I have PAL DVB-T here and not NTSC.

However this guide should work for you:  [https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

I'm sure others who have contributed to this thread should be able to assist too.

Rob

---

### Post by SirShaggy on 2007-02-18
> **Erlander said:**
> Sorry Sir,

I fear I won't be much use to you as one of my problems was I have PAL DVB-T here and not NTSC.

However this guide should work for you:  [https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

I'm sure others who have contributed to this thread should be able to assist too.

Rob

Thank You, I got more info I needed. Just a little to go. I did find out that my sound in the FM Tuners does not/will not work with the 2.6.17 kernels. I am in the process of compiling a new kernel. Thanks again,
SirShaggy

---

