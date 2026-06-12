---
title: "ATI integrated 3200 underscan"
date: 2008-10-27
forum: Multimedia Software
---

### Post by Kryspy on 2008-10-27
Hi,

I installed ubuntu 8.04 and after installing the ATI video drivers I still get a 1 1/2 black border around my LCD TV screen.   I used the envyNG option.

In the CCC the scale to full screen is checked off.  I know the windows CCC allows a slider to adjust the underscan to fullscreen.

I am using HDMI to my TV but could use DVI to HDMI if it would help.

Anyone else get this or know of a fix?

Thanks in advance,

Kryspy

---

### Post by Kryspy on 2008-10-28
So,

To answer my own question.  I tried out 8.10 this morning of Ubuntu and it detcted and installed the ATI drivers automatically for me.  Only problem now is about 5% overscan enough that the menu bars are off the screen.

Kryspy

---

### Post by khmr33 on 2008-12-28
same problem here

only solution I've found to underscan was 

```
#$ sudo aticonfig --set-dispattrib=tmds2:SizeX=1920
#$ sudo aticonfig --set-dispattrib=tmds2:SizeY=1080
#$ sudo aticonfig --set-dispattrib=tmds2:PositionX=0
#$ sudo aticonfig --set-dispattrib=tmds2:PositionY=0
```

this "fixes" the underscan until reboot... then X crashes and I can't log in. I have to boot into recovery, fix X, then redo fglrx, then black borders reappear.

This ONLY happens with my HDMI connection. If I switch to VGA and reinstall FGLRX everything works fine... I can even get flicker free fullscreen video in compiz fusion. 

Asus M3A78-EMH HDMI
Samsung LN52A650

---

### Post by trazalca on 2009-01-02
khmr33 i have your same problem with my hd2600 pro and samsung le40m87, dvi to hdmi cable, someone can help us for this?? Thanks

---

### Post by markbuntu on 2009-01-02
Which driver version are you guys using?

Have you tried toggling the tv-overscan option. There are a number of tv options in aticonfig.

aticonfig --help

---

### Post by khmr33 on 2009-01-02
I had just finished installing the most recent ATi driver 8.12 I think. As far as I can tell it's not a tv-output problem because we're not using s-video or component out from a stand alone radeon card. At least I'm not.

HDMI -> HDMI and DVI -> HDMI connected to an HDTV is usually detected as a really big PC Monitor. My Samsung actually expects PC's to be connected via HDMI DVI and VGA and this works perfect on VGA under linux and perfect under all three in XP pro. 

8.12 under VGA in Linux is the first time I've gotten fullscreen flicker-free (though not tear-free) video with compiz fusion active. This same PC under XP plays all sorts of HD content including HD-DVD's perfect but maybe I expect too much too soon from the Linux drivers.

The only difference I can find between the Linux and Windows drivers in this regard is a slider in the XP CCC that controls a 0% - 15% amount of overscan.
When you install a fresh XP ATi driver the black border exists as well but this slider in CCC adjusted to 0% fixes it no problem.

However there seems to be no manual equivalent in aticonfig or certainly not in the linux CCC. Like I said the only commands that even work I mentioned above and they somehow crash X to a black screen on reboot.

I originally theorized this was strictly an HDMI problem, so after a few weeks of living with a VGA connection (which would be fine if my goal wasn't HD video playback) I came into a DVI -> HDMI cable. Hoping beyond hope that there was some secret DVI support I wasn't aware of. It's the same problem. Maybe some secret conflict with the xorg.0.log I'm not aware of or my lack of sacrificial lambs, chickens, or children. heh...

---

### Post by markbuntu on 2009-01-04
The linux ati driver is still very much a work in progress and the Catalyst Control Center even more so. The driver is ahead of the CCC so you need to use the command line utility aticonfig to access these functions.

Ati should have bitstream HD support in the driver by the jan or feb driver release. Some of the libs have been in the driver now for the last few releases so it is coming very soon along with a better CCC.

Flickering and tearing, while reduced, will not be completely solved until DRI2 is released with the new xserver 1.0.16 which will be incorporated into Ubuntu 9.04 which will be released in April. DRI2 was originally scheduled to be released last june but was held up due to some sudden changes by Intel that needed to be incorporated.

---

### Post by tobbe75 on 2009-01-24
> **khmr33 said:**
> same problem here

only solution I've found to underscan was 

```
#$ sudo aticonfig --set-dispattrib=tmds2:SizeX=1920
#$ sudo aticonfig --set-dispattrib=tmds2:SizeY=1080
#$ sudo aticonfig --set-dispattrib=tmds2:PositionX=0
#$ sudo aticonfig --set-dispattrib=tmds2:PositionY=0
```

this "fixes" the underscan until reboot... then X crashes and I can't log in. I have to boot into recovery, fix X, then redo fglrx, then black borders reappear.

This ONLY happens with my HDMI connection. If I switch to VGA and reinstall FGLRX everything works fine... I can even get flicker free fullscreen video in compiz fusion. 

Asus M3A78-EMH HDMI
Samsung LN52A650

I have the exact same experience, but have found a workaround that works for me, so I thought I'd share this.
the above commands I have put in a script that runs automatically when my X session starts. (System->Settings->Sessions).
So this fixes my screen so it's fullscreen, but to avoid the X crashing at reboot I made this little workaround:
before I run the ati-config the first time, I take a copy of the amdpcsdb:
```
sudo cp /etc/ati/amdpcsdb /etc/ati/amdpcsdb.working
```

Then I but another script in /etc/init.d/ called restore-ati-config.sh:
```
#/bin/sh
cp /etc/ati/amdpcsdb.working /etc/ati/amdpcsdb
```
 that will copy amdpcsdb.working to amdpcsdb.
Then I linked this into rcS.d:
```
ln -s /etc/init.d/restore-ati-config.sh /etc/rcS.d/S50restore-ati-config.sh
```
Now this will be run in Singe User Mode during boot, before X is started.

This avoids the crash for me. Would be interesting to know if this works for anyone else? Also this is maybe not the best workaround, but it works for now.
When are ATI going to give us real divers and utilities on Linux? This 
same issue was easy to fix in windows ccc (the underscan/overscan slider).

And also I want to thank you for theese commands, without them I've never worked it out. Was almost gonna go for windows when this saved my Ubuntu installation ;-)

---

### Post by markbuntu on 2009-01-25
Have you reported this to ati?
It is difficult for them to fix things they do not know about but they are very good about fixing things they do know.

---

### Post by xtreme- on 2009-01-31
Thanks, 
This fixed it for me, running Arch Linux 64 bit w/ fglrx 8.56.4.:)

---

### Post by leprotic on 2009-03-06
Hi. I am a total newbie and my ubuntu experience is close to zero. I have the same problem with a 2600 XT. I'm going to try tobbe75's suggestion but I'm afraid of messing it up. (For starters, I don't know how to add scripts on start-up) Can anyone help me with a step-by-step guide? I'd be obliged. I don't want to switch back to windows for this problem.

---

### Post by leprotic on 2009-03-07
> **leprotic said:**
> hi. I am a total newbie and my ubuntu experience is close to zero. I have the same problem with a 2600 xt. I'm going to try tobbe75's suggestion but i'm afraid of messing it up. (for starters, i don't know how to add scripts on start-up) can anyone help me with a step-by-step guide? I'd be obliged. I don't want to switch back to windows for this problem.

bump!

---

### Post by taukappamu on 2009-03-31
> **tobbe75 said:**
> I have the exact same experience, but have found a workaround that works for me, so I thought I'd share this.
the above commands I have put in a script that runs automatically when my X session starts. (System->Settings->Sessions).
So this fixes my screen so it's fullscreen, but to avoid the X crashing at reboot I made this little workaround:
before I run the ati-config the first time, I take a copy of the amdpcsdb:
```
sudo cp /etc/ati/amdpcsdb /etc/ati/amdpcsdb.working
```

Then I but another script in /etc/init.d/ called restore-ati-config.sh:
```
#/bin/sh
cp /etc/ati/amdpcsdb.working /etc/ati/amdpcsdb
```
 that will copy amdpcsdb.working to amdpcsdb.
Then I linked this into rcS.d:
```
ln -s /etc/init.d/restore-ati-config.sh /etc/rcS.d/S50restore-ati-config.sh
```
Now this will be run in Singe User Mode during boot, before X is started.

This avoids the crash for me. Would be interesting to know if this works for anyone else? Also this is maybe not the best workaround, but it works for now.
When are ATI going to give us real divers and utilities on Linux? This 
same issue was easy to fix in windows ccc (the underscan/overscan slider).

And also I want to thank you for theese commands, without them I've never worked it out. Was almost gonna go for windows when this saved my Ubuntu installation ;-)

I have same problem on my 42" Philips LCD TV. Tried to follow your instruction but cannot work. Possible to elaborate step by step?

Thanks.

---

### Post by gier on 2009-03-31
I've been grappling with this problem as well, for a couple of days. Much googling has finally uncovered this at the Phoronix forums:

[http://www.phoronix.com/forums/showthread.php?t=10073&page=4](http://www.phoronix.com/forums/showthread.php?t=10073&page=4)

After messing about for a bit, I've figured out a more direct way of solving this.

You need to change the Persistent Configuration Store (PCS) database, which fortunately is a flat file.

First, make a backup of the pcs database, as so:

```
sudo cp /etc/ati/amdpcsdb /etc/ati/amdpcsdb.backup
```

Next, edit the file */etc/ati/amdpcsdb* as so:

```
sudo nano /etc/ati/amdpcsdb
```

See the attached file fragments below. The lines you need to add are in red. Make sure you put them under the right sections!

```

AMDPCSDBV1
[AMDPCSROOT/SYSTEM/MCIL]
PXACAutoSwitch=V0
PXDCAutoSwitch=V0
CVRULE_CUSTOMIZEDMODESENABLED=V1
DFP_AddHDTVPixelFormats=V2
DALLinuxSupport=V1
DALNonStandardModesBCD=R140010500000006017921344000000601800144000000060185613920000006016001200000000601280076800000060144009000000006012800960000000601680105000000060
DALRULE_ADDNATIVEMODESTOMODETABLE=V1
DALRULE_ALLOWMONITORRANGELIMITMODESCRT=V0
DALRULE_DYNAMICMODESUPPORT=V1
DALRULE_GetLCDFakeEDID=V1
DALRULE_GetTVFakeEDID=V1
DALRULE_NOFORCEBOOT=V1
DALRULE_POWERPLAYDISREGARDDISPLAY=V1
DALRULE_RESTRICTDISPLAYSBASEDONPANELRES=V0
DALRULE_REGISTRYACCESS=V1
GCORULE_FlickerWA=V1
GCORULE_LCDValidatePixelClkOnly=V1
GXOM5XDisableLaneSwitch=V1
R6LCD_RETURNALLBIOSMODES=V1
TVEnableOverscan=V1
UvdEnabled=V1
Gxo50HzTimingSupport=V1
Gxo24HzTimingSupport=V1
Gxo2530HzTimingSupport=V1
[COLOR="Red"]DigitalHDTVDefaultUnderscan=V0[/COLOR]

```

Scroll down further until you find:

```

[AMDPCSROOT/SYSTEM/DDX]
OGLFMTA2R10G10B10Enable=V0
[COLOR="Red"]EnableRandR12=SFALSE[/COLOR]

```

The first part is turning off the Underscan default, as given in the earlier Phoronix link. The second part is disabling the RandR, since it wouldn't work otherwise ... or maybe it would. Give it a try without. I didn't actually try it that way.

Anyway, hope that helped.

gier

---

### Post by taukappamu on 2009-04-01
Thanks gier. 

However, now I'm having the opposite problem: the sides of the screen, about the same amount as the previous black borders, are out of the LCD TV.

Thanks again if you can help this noob here

---

### Post by taukappamu on 2009-04-01
my amdpcsdb as follow:

AMDPCSDBV1
[AMDPCSROOT/SYSTEM/MCIL]
PXACAutoSwitch=V0
PXDCAutoSwitch=V0
CVRULE_CUSTOMIZEDMODESENABLED=V1
DALLinuxSupport=V1
DALNonStandardModesBCD=R140010500000006017921344000000601800144000000060185613920000006016001200000000601280076800000060144009000000006012800960000000601680105000000060
DALRULE_ADDNATIVEMODESTOMODETABLE=V1
DALRULE_ALLOWMONITORRANGELIMITMODESCRT=V0
DALRULE_DYNAMICMODESUPPORT=V1
DALRULE_GetLCDFakeEDID=V1
DALRULE_GetTVFakeEDID=V1
DALRULE_NOFORCEBOOT=V1
DALRULE_POWERPLAYDISREGARDDISPLAY=V1
DALRULE_RESTRICTDISPLAYSBASEDONPANELRES=V0
GCORULE_FlickerWA=V1
GCORULE_LCDValidatePixelClkOnly=V1
GXOM5XDisableLaneSwitch=V1
R6LCD_RETURNALLBIOSMODES=V1
TVEnableOverscan=V1
UvdEnabled=V1
DigitalHDTVDefaultUnderscan=V0
DigitalHDTVDefaultOverscan=V0
[AMDPCSROOT/SYSTEM/2ID-1002-791E-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7941-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-796E-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9610-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9611-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9614-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7124-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7105-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-710f-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-712e-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-712f-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-710e-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7125-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7104-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-940b-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-940a-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-940f-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9447-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7152-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7172-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7173-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7153-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-71d2-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-71f2-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-71fa-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-71da-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-728c-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-72ac-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-95cc-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-958d-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-958c-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9511-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-949c-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-949f-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-949e-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9444-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9446-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9456-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-71bb-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-719b-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-95cd-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-95ce-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-95cf-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-3151-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9452-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9519-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/DDX]
OGLFMTA2R10G10B10Enable=V0
EnableRandR12=SFALSE
MultiviewXineramaNo3D=V1
UseFastTLS=S1
Centermode=Soff
[AMDPCSROOT/SYSTEM/DDX/RECENTMODE/SCREEN00]
Width=V1920
Height=V1080
Refresh=V60
[AMDPCSROOT/SYSTEM/BUSID-1:5:0-0/MCIL]
DAL_ACEspectReady=V0
DALLastSelected=V2
DALLastConnected=V2
DALLastTypes=V129
DALObjectData0=R010000000100000000000000010000000100000000000000010000000100000000000000010000000100000000000000010000000200000000000000010000000200000000000000030000000200000001000000030000000200000001000000010000000100000000000000010000000100000000000000010000000100000000000000000000000000000000000000010000000200000000000000000000000000000000000000010000000200000000000000020000000000000001000000
DALSelectObjectData0=R010000000100000000000000010000000100000000000000010000000100000000000000010000000100000000000000010000000200000000000000010000000200000000000000030000000200000001000000030000000200000001000000010000000100000000000000010000000100000000000000010000000100000000000000000000000000000000000000010000000200000000000000000000000000000000000000010000000200000000000000020000000000000001000000
DALCurrentObjectData=R010000000200000000000000000000000000000000000000
DALR6 DFPI 2_MaxModeInfo=R000000008007000038040000000000003C000000
DAL_DFP2ColorTemperatureSource0C41151B=R0000000064190000
AsicOnLowPower=V0
[AMDPCSROOT/SYSTEM/BUSID-1:5:0-0/DDX]
Centermode=Son
[AMDPCSROOT/SYSTEM/BUSID-1:5:0-0/LibXUtil/Display1]
Map=V128
Enable=V1
[AMDPCSROOT/SYSTEM/LibXUtil/Display1]
Map=V128
Enable=V1
[AMDPCSROOT/SYSTEM/LDC]
LastViewedPage=SDisplay Manager
LastSelectedDevice=S296:38416:4098:53248:5208|1

---

### Post by gier on 2009-04-01
Well, in so far as I know, the line:

DigitalHDTVDefaultOverscan=V0

doesn't actually do anything at all.

I have the same overscan problem as you do. The only solution that I've found for that so far is TV dependent. In other words, if you have an LCD TV that can disable overscan, you're sorted. Otherwise, you're smegged.

I don't have a Philips, so I'm not sure if it does have that ability. Try checking around the options in the TV's menu.

For the Panasonic, it's literally turning off "Overscan"

For the Sony Bravia, I think it's turning on "Full Pixel".

For the Sharp Aquos, no joy.

I've got a Tosh, an LG Scarlet and an old Samsung that I haven't checked yet ... and don't ask me why I have so many tellys ... :D

---

### Post by taukappamu on 2009-04-01
Thanks again gier. Was very excited about Ubuntu, but now it's getting frustrating

---

### Post by taukappamu on 2009-04-01
Finally, 1920 x 1080 resolution without any under/over scan! Finally found the overscan problem on my Philips 42PFL7603/98.

gier, thanks for your help & inspiration

---

### Post by gier on 2009-04-02
Good stuff, bro. I'm glad to be of help.

The frustration is part of the experience, I think ... or summink like that. :D

---

### Post by kaivai on 2012-11-26
gier!!! You were right! It worked!

I don't know if any of you are still having problems with this but taukappamu's fix from phoronix works for me!

The key part though seems to be that the amdpcsdb file seems to be generated on boot or shutdown or something. Every time I restart my computer it does not work

*BUT*

if you make the changes to the file, then restart your xsession - VOILA! you get that beautiful full screen again.

Here is how I did it:

(and I'm sorry, I'm using Debian and Gnome right now, the commands may vary)

* CTRL+ALT+F2 to go to a terminal that isn't run by your xsession
* Login
```

/etc/init.d/gdm3 stop
startx

```

I'm going to try adding something to my startup script that makes the changes and restarts my xsession.

---

### Post by kaivai on 2012-11-26
I posted this in reply to myself on the linux question boards - but this automatically gets rid of the borders on boot. no need to restart the xserver.


I wrote a script that writes the additions to /etc/ati/amdpscdb on startup. Before applying this, you should probably read the following:

**What you should know before doing this:**
[INDENT][INDENT]
```

man update-rc.d

```
Linux uses run levels in which it starts programs as the computer boots.

0       --> when the computer shuts down
s or 1  --> when the computer boots
2,3,4,5 --> different run levels (you can see which programs boot in each in /etc/rc2.d/,/etc/rc3.d/, /etc/rc4.d/ etc...
6       --> a reboot

if you wanted to jump straight to a run level you can use the command telinit 3, telinit5 etc.

Note that apparently distrobutions can choose to have programs run at different run levels. I cannot remember the man page that I read this in. sorry.
[/INDENT][/INDENT]

**Explanation:**
In Debian 6.3 - FGLRX runs it's first script in run level 2.
I assumed that this is where it generates /etc/ati/amdpcsdb
so I added a script that runs at that run level (actually I was impatient and made it start at 2,3,4,and 5)
the script looks for the line:

Gxo50HzTimingSupport=V1/Gxo50HzTimingSupport=V1 
and adds 
DigitalHDTVDefaultUnderscan=V0 
to the next line

check your amdpcsdb to make sure that line exists, if it does not, choose another line under the same heading (the part in brackets)



**Instructions:**
[INDENT]
- ```
cd /etc/init.d
```
- ```
nano fglrxfix
```
- enter the following:
```

	# FGLRX underscan fix
	#-----------------------------

sed 's/Gxo50HzTimingSupport=V1/Gxo50HzTimingSupport=V1\nDigitalHDTVDefaultUnderscan=V0/g' </etc/ati/amdpcsdb>wpbuffer	
sudo cp wpbuffer /etc/ati/amdpcsdb
sudo rm wpbuffer

exit0

```

- ```
chown root fglrxfix
``` #makes root owner of fglrxfix
- ```
chmod 4755 fglrxfix
``` #makes fglrxfix executable as su

- ```
update-rc.d fglrxfix start 20 2 3 4 5 .
``` #makes fglrxfix run on startup (basically)

-you're done
[/INDENT]

This seems like a giant pain in the ***, but it's waaaaaaaaaaaaaay better than having to exit and restart the xserver every time you log in. This method works with multiple monitors.

Cheers folks!

---

### Post by oldos2er on 2012-11-26
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

