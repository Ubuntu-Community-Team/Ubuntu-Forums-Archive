---
title: "New Install - no TV video displayed"
date: 2010-10-25
forum: Mythbuntu
---

### Post by Epiphyte on 2010-10-25
OK. I was persuaded to install Mythbuntu 10.10 on my older machine (which was running D1's MythTV).

It appeared to install OK (albeit without any fancy peripherals. ). 

When I rebooted the machine, all I got was "mythbuntu" on a black screen with 5 red dots underneath. :frown:

(Except... I did ask it to install TV out. That seemed strange because I wasn't asked to nominate a tuner card).

The machine boots and runs the frontend from the CD nicely. After that - no joy.

What do I do now? Do I:

1] Give up.
2] Download an older distro of Mythbuntu, and try that?

The doco is of no help.

Can anyone help here :confused:

---

### Post by tonycollinet on 2010-10-25
I had exactly that same issue a few days ago.

1 - do not select nvidia drivers during the install process.
2 - ensure you are connected to the internet if possible during the install.

3 - Nvidia drivers can be installed after ubuntu installation. However, I've still not got that to work yet. (an illustration of why linux will never be mainstream, if these issues cannot be sorted more simply)

4 - If you want to get it to boot now without re-installing try - esc (repeat) during boot to get to the recovery menu (you may have to try a time or three), and select "drop to terminal" (or similar)

Then 

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If that fails, suggest a re-install as described above.

---

### Post by Woodwa on 2010-10-25
Maybe you try a vanilla Ubuntu install..

you can download myth once installed via synaptic..

does the D1 sport Nvidia graphics??

---

### Post by Epiphyte on 2010-10-25
*[COLOR="DarkRed"]tonycollinet[/COLOR]*:

Thanks, that is working now, without the NVIDIA graphics support. **But**... it raises a whole HEAP of issues. 

The issues are:
1] I have NO network connectivity.
2] My NVIDIA graphics card is not supported.
3] My remote is not recognised.

ALL These are show stoppers !!!

Should I just raise them one at a time on this forum? Can you point me to some real documentation on Mythbuntu?

*[COLOR="DarkRed"]Woodwa[/COLOR]*:

Yes, the D1 did support the NVIDIA graphics card !

Any help please ?

---

### Post by LowSky on 2010-10-25
> **Epiphyte said:**
> *[COLOR="DarkRed"]tonycollinet[/COLOR]*:

Thanks, that is working now, without the NVIDIA graphics support. **But**... it raises a whole HEAP of issues. 

The issues are:
1] I have NO network connectivity.
2] My NVIDIA graphics card is not supported.
3] My remote is not recognised.

ALL These are show stoppers !!!

Should I just raise them one at a time on this forum? Can you point me to some real documentation on Mythbuntu?

*[COLOR="DarkRed"]Woodwa[/COLOR]*:

Yes, the D1 did support the NVIDIA graphics card !

Any help please ?



Please explain your issues.
1) are we talking wireless or wired connection for internet connectivity?

2) What Nvidia Card? Did you take a look at this:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

3) What Remote?
Did you use Mythbuntu-Control-Center to pick the correct remote for LIRC?

---

### Post by Epiphyte on 2010-10-25
[COLOR="DarkRed"]*LowSky*[/COLOR]:

My answers are as follws:

1. The net connection is a wired one. I cannot ping my router. I set up my network with fixed IP addresses, but can't find where to set up DNS server addresses see (***newb warning***) below.

2. No, I hadn't seen this but I will investigate when I get the net connection working as I may have to upgrade packages etc...

3. There appears to be no "correct" remote. The remote is a custom "special" , built for the D1. I would have to dig around in the D1 source (yes, I have a second of these machines) to find any relevant data.

I almost forgot.... my video capture card is an AVer Media
AVerTV DVB-T 771. Apparently this is well supported but I couldn't see it in the backend configuration process.

Also ... [COLOR="Red"]**NEWB WARNING**[/COLOR]. I am a linux novice so I may have to ask stupid questions at first.

Thank you all for your help so far.... :)

P.S. Sorry LowSky - I see you are in the US. The D1 was a commercially-produced, Australian MythTV appliance. The company went bust a few years ago. This is what it lookes like: [http://www.cnet.com.au/d1-home-media-centre-240053886.htm]("http://www.cnet.com.au/d1-home-media-centre-240053886.htm")

---

### Post by tonycollinet on 2010-10-25
Regarding network settings - you can enter dns and gateway in the network applet (edit connections using the icon top right of screen - can't remember whether you must right or left click it to get there)

noob here also (just a day or two ahead of you) - hopefully we can muddle through the nvidia stuff between us... :-)

---

### Post by LowSky on 2010-10-25
The remote is more than likely easily figured out. It is more than likely a rebranded device.
open a terminal
type ```
lsusb
```
the l is a lower-case L, the info it tells you will list everything connected by usb

a similar code ```
lspci
``` will tell you everything connected to a pci/agp port

**tonycollinet **has the right info for setting up your internet connection

I took this from my tutorial for setting up a different DVB tuner card but it should work decently:

To get the card running open the MythTV Backend Setup (Applications>System>MythTV Backend Setup)

Once it is running go to Capture Cards, choice #2.
Choose new capture card, 
At card Type, pick DTB DTV.


 Go to video sources, pick your options, I had to setup an account with SchedulesDirect.org, so that I could get local channel guide information in the USA. Your country may have other options. Not sure for Australia..

 Next go to Input Connections
 Edit channels and directories as needed. Sorry I can't really help with this. A word of suggestion is learn the directories that data is stored. If you setup your machine and didn't use the entire disk, make sure to change the directories for recorded data as they will fill the root partition if you are not careful. Remember that the directories you create need to have write access for the MythTV group. Since my /home directory was on a separate 500GB hard drive I wanted to use that. I created a Folder named within the /home/mythtv/ folder. I added over 80 or so hours of record time doing this. I found out 1.2TB is roughly 200+ hours of recording time for HD video.

Close MythTV Backend by hitting ESC, it will then ask to fill the database, let it. The Database will take a good amount of time, and may look like it is running in a loop. Don't worry its collecting data for 14 days worth of channel listings if you used ShedulesDirect.org. This may take up to a half hour. The more channels you have the longer.

 Now go to Applications >Multimedia > MythTV Frontend.

The next part is from my setup, but for many it might be required (I would love feedback).

First go to Utilities / Setup, its the last option. Choose Setup, then Appearance.

The first page is to choose your theme (A little about me: my choice is MythCenter-wide).
Next page is important: If you have more than one monitor, pick the one you want to display the GUI on. The second is the Monitor Aspect Ratio, be sure to set it to your TV or monitor's correct display size, Mine is 16:9 your's may be 16:10 or 4:3. A good rule of thumb I follow is most monitors and HDTV's are 16:9, some PC monitors are 16:10, SDTV is 4:3. Failure to set this might result in a horrible stretched picture. Also on this page is to hide the mouse cursor. If you want to use a mouse over a keyboard or remote, then uncheck the box.
The next few pages I don't touch, sorry your on your own if you want to edit those.

 Now back to Utilities / Setup > Setup

Choose TV Settings. Again for most of this its all your preference. But one thing I found odd and I needed it fixed. On the Page 3/8 (labeled Playback Profiles), I had to set the Current Video Playback Profile to High Quality. If you have a newer model Nvidia card (8500 or better) you can use VDPAU

---

### Post by Valen00 on 2010-10-25
Is there any particular reason your not using DHCP?
Its probably easiest, if you want it on a fixed IP, set a lease in your modem or don't worry about it for the time being, get everything working then add the hassle of that.

As far as remotes go I use [http://www.shintaro.com.au/products/06_keyboards_mice/keyboards/SH-KEYRF/](http://www.shintaro.com.au/products/06_keyboards_mice/keyboards/SH-KEYRF/)
and its brilliant, I use the keyboard all the time to google stuff about shows I'm watching.

---

### Post by LowSky on 2010-10-25
> **Valen00 said:**
> Is there any particular reason your not using DHCP?
Its probably easiest, if you want it on a fixed IP, set a lease in your modem or don't worry about it for the time being, get everything working then add the hassle of that.
More than likely the OP has DSL, or a preexisting setup that he rather not mess up.
> 
As far as remotes go I use [http://www.shintaro.com.au/products/06_keyboards_mice/keyboards/SH-KEYRF/](http://www.shintaro.com.au/products/06_keyboards_mice/keyboards/SH-KEYRF/)
and its brilliant, I use the keyboard all the time to google stuff about shows I'm watching.



Lets not recommend any new equipment until we know it cant be fixed, which I'm betting it can be easily working in a few moments.

---

### Post by Epiphyte on 2010-10-25
OK GUYS - we are nearly there !!!

The system has allowed me to download Aussie EPG data !

The reason I'm not using DHCP is that.... err.... I've forgotten. Anyway, the network works fine now!

I attempted to try to install some updates to get the NVIDIA card up & running, but I might have broken something. The system tries to show live TV, but then quickly reverts back to an Ubuntu/xfce login screen, asking me to login for a session. What have I done :confused:

The remote will have to wait till a bit later I'm afraid.

Thanks for your help so far :) 

Please keep it coming [-o<

---

### Post by nickrout on 2010-10-25
> **Epiphyte said:**
> OK GUYS - we are nearly there !!!

The system has allowed me to download Aussie EPG data !

The reason I'm not using DHCP is that.... err.... I've forgotten. Anyway, the network works fine now!

I attempted to try to install some updates to get the NVIDIA card up & running, but I might have broken something. The system tries to show live TV, but then quickly reverts back to an Ubuntu/xfce login screen, asking me to login for a session. What have I done :confused:

The remote will have to wait till a bit later I'm afraid.

Thanks for your help so far :) 

Please keep it coming [-o<

I don't think you have told us what nvidia card that machine has.

---

### Post by Epiphyte on 2010-10-26
Oops  :oops:


The best I can find out is that it is an NVIDIA NV18 GeForce4 MX440 AGP8x.

BTW, shouldn't this at least play some crappy TV with the standard video driver?

I have downloaded a driver from the nvidia website. It is titled "NVIDIA-Linux-x86-96.43.18-pkg1.run". Where do I put it & how do I now install it?

I looked at the page recommended here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"). I was unable to activate restricted drivers as recommended under "Ubuntu 9.10 and Ubuntu 10.04"

I then went to synaptic package manager and couldn't seem to find linux-headers-XXX and linux-restricted-modules-XXX as suggested.

What now?

---

### Post by Epiphyte on 2010-10-26
[FONT="Arial"]Just for convenience I have uploaded a file called[/FONT] *hwconfig.txt.* [FONT="Arial"] This is a listing of the command[/FONT] [FONT="Courier New"]lshw[/FONT].

[FONT="Arial"]Strangely it says I have the nouveau driver installed for my card nvidia card. I don't remember installing that !

Thanks guys.[/FONT]

---

### Post by LowSky on 2010-10-26
Epiphyte the noveau driver is used by default. If you want the proprietary driver, folow these instructions

open a terminal

copy and past these commands

```
sudo apt-get --purge remove xserver-xorg-video-nouveau 
```

```
sudo apt-get install nvidia-current
```

NOW Reboot the machine, and reopen a terminal, copy this command
```
sudo nvidia-xconfig
```

you might have to reboot again to get things working correctly.


Finally to change settings fo r resolution or enable S-video

```
gksu nvidia-settings
```
```

```

```

```

---

### Post by Epiphyte on 2010-10-26
LowSky:

Thanks for that. Should I install the driver I downloaded somehow?

Is this what is causing the lack of TV picture?

---

### Post by nickrout on 2010-10-26
Don't forget this is a legacy card requiring the 96.43 series driver. In any event the ubuntu system should find the right driver.

I believe what you wrote will get the 195 series driver which will not work with this card!!

---

### Post by nickrout on 2010-10-26
> **Epiphyte said:**
> LowSky:

Thanks for that. Should I install the driver I downloaded somehow?

Is this what is causing the lack of TV picture?

Absolutely not. Use the ubuntu packaging system!

---

### Post by Epiphyte on 2010-10-26
nickrout:

Sorry, I'm a bit lost here. 

I haven't, yet, installed any new driver for the nvidia card. What should I install? 

I have graphical video output  from the PC, but the machine seems to not be picking up TV video from the tuner card OR not transcoding it properly, in order to display it (I don't know which). I know it "sees" the transport signal, since it detected xx channels correctly when I did a channel scan.

The damn thing should work. ](*,)

---

### Post by nickrout on 2010-10-26
I assume you have run mythtv-setup? 

Can you watch any of the recorded streams using mplayer? or vlc? The recordings are (by default) in /var/lib/mythtv/recordings/

---

### Post by Epiphyte on 2010-10-26
nickrout:

yes, I have run mythtv-setup (or the backend setup util from the myth menu) - a few times trying to figure out what I have done wrongly.

I don't think I have any recordings to view! I'm still strugging with the remote setup as well (the driver is "d1ldo", a "special", I think).

---

### Post by Epiphyte on 2010-10-26
UPDATE:

**[COLOR="DarkOrange"]I now have TV picture[/COLOR]** =D> 

It seems that the problem has to do with signal quality and video buffering.

I am 100kms (80 miles) line-of-sight from the transmission antenna. The reception is greatly affected by intervening atmospheric conditions. I get lots of "artifact" in the signal on hot, hazy and smoggy days. (Yep, summer is coming so... joy oh joy !!)

[COLOR="DarkRed"]*Any thoughts on tweaking here ?*[/COLOR]

Final question (vaguely) on this topic.

***Should I attempt to install an nvidia driver, and how?***

Many thanks to LowSky, nickrout, tonycollinet for their excellent help & assistance.

---

### Post by nickrout on 2010-10-26
> **Epiphyte said:**
> UPDATE:

**[COLOR="DarkOrange"]I now have TV picture[/COLOR]** =D> 

It seems that the problem has to do with signal quality and video buffering.

I am 100kms (80 miles) line-of-sight from the transmission antenna. The reception is greatly affected by intervening atmospheric conditions. I get lots of "artifact" in the signal on hot, hazy and smoggy days. (Yep, summer is coming so... joy oh joy !!)

[COLOR="DarkRed"]*Any thoughts on tweaking here ?*[/COLOR]

Final question (vaguely) on this topic.

***Should I attempt to install an nvidia driver, and how?***

Many thanks to LowSky, nickrout, tonycollinet for their excellent help & assistance.

yes, try ```
sudo aptitude install nvidia-96
sudo nvidia-xconfig
gksu nvidia-settings
```

---

### Post by LowSky on 2010-10-27
> **nickrout said:**
> yes, try ```
sudo aptitude install nvidia-96
sudo nvidia-xconfig
gksu nvidia-settings
```

Nickrout, we already got nvidia working for him, no need to install it again.

Epiphyte you may need an antenna pre amp
like this
[http://www.amazon.com/Winegard-AP-8700-Preamplifier-Noise-Antennas/dp/B001DFZ5EW/ref=pd_cp_e_0](http://www.amazon.com/Winegard-AP-8700-Preamplifier-Noise-Antennas/dp/B001DFZ5EW/ref=pd_cp_e_0)

---

### Post by nickrout on 2010-10-27
> **LowSky said:**
> Nickrout, we already got nvidia working for him, no need to install it again.



Says who, I don't see that post?

---

