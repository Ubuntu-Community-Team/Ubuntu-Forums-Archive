---
title: "Open ATI Drivers &amp; Tv-out with S-video in Ubuntu 9.04"
date: 2009-04-24
forum: Multimedia Software
---

### Post by nibbana84 on 2009-04-24
Hi everybody, 
since the following products series have been moved to the legacy software from ATI:

9500 9550 9600 9700 9800 X300 X550 X600 X700 X800 X850 X1050 X1300 X1550 X1600 X1650 X1800 X1900 Xpress X1200 X1250 X2100 

people like me who own one of this video cards cannot use proprietary drivers anymore.

My card is an X1400 and **_I cannot use tv-out with s-video anymore_** with open drivers. 
The procedure should be (quoting [http://www.x.org/wiki/radeonTV):](http://www.x.org/wiki/radeonTV):)

```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xrandr --output S-video --set tv_standard ntsc
```

and in case S-video is not recognized, adding in xorg.conf 
```
Option "ATOMTvOut" "TRUE"
``` 

But this didn't work for me: the monitor start flickering and the TV gets black with white stripes.

I saw around the Web that this is because of some sort of bug in the open drivers about this manner, but since the page [http://www.x.org/wiki/radeonTV](http://www.x.org/wiki/radeonTV) looks quite old I thought the problem might be "fixable".

Since ATI does not support us anymore, please if someone knows how to fix this problem, that would be very much appreciated.

Thank you very much,

---

### Post by nibbana84 on 2009-04-25
Anybody?

---

### Post by nibbana84 on 2009-04-25
Please?

---

### Post by partofthething on 2009-04-26
Now that 9.04 is released and we're required to use the open drivers (which work great with compiz and everything!), all we need is s-video out and I'll be extremely happy. I'm in the same boat here.

---

### Post by nibbana84 on 2009-04-26
> **partofthething said:**
> Now that 9.04 is released and we're required to use the open drivers (which work great with compiz and everything!), all we need is s-video out and I'll be extremely happy. I'm in the same boat here.

Exactly! The 3d acceleration works even better with open drivers with my video card. But unfortunately I definetelly need the s-video out. I can't believe I must use Windows. I hope ATI drivers developers realize the priority of this bug!

In the meantime, I encourage everybody to say something about it, tt least in this way we realize how many we are...

I have not idea how many people use those video cards, but I suppose we are quite a few!

---

### Post by TusharG on 2009-04-28
Yes even I have noticed that S-Video has stopped working in 9.04. I have ATI Readon Xpress 200M card and TV out was working perfectly fine till 8.04 and even in debian Lenny. Not sure why in 9.04 it is not working.

---

### Post by aquanim on 2009-04-28
same situation here. 3D effects are way better than before without any activation of drivers etc. however no S-Video. i am still loking for a workarround

---

### Post by nibbana84 on 2009-04-28
> **aquanim said:**
> same situation here. 3D effects are way better than before without any activation of drivers etc. however no S-Video. i am still loking for a workarround

If anybody has a solution please share it with us.

---

### Post by ProteinPappa on 2009-04-29
I too desire this feature for my X700.

---

### Post by Mandev on 2009-04-30
I'm with the same problem with Radeon mobile 9600. And I think we are not so few. And I believe Ubuntu developers will do something. I'll never go back to Windows OS. ATI driver on it also was trouble.
Cheers everybody!
;)

PS
If somebody find a solution pleas [email]ivanmandev@abv.bg[/email]

---

### Post by N'ko on 2009-05-01
On a HP NC6000 with Radeon mobility 9600, typing the following in order in the terminal, works.
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600

Problems I have are, the desktop is too large for the TV screen, cutting off part of the desktop.  Does anyone know how to shrink the output to the TV.  Also when I try to play a DVD in VLC there is no output of the video on the TV but everything is OK on the laptop's LCD screen.  This probably has somethings to do with 3d acceleration.

---

### Post by nibbana84 on 2009-05-02
> **N'ko said:**
> On a HP NC6000 with Radeon mobility 9600, typing the following in order in the terminal, works.
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600

Problems I have are, the desktop is too large for the TV screen, cutting off part of the desktop.  Does anyone know how to shrink the output to the TV.  Also when I try to play a DVD in VLC there is no output of the video on the TV but everything is OK on the laptop's LCD screen.  This probably has somethings to do with 3d acceleration.

Before you type those commands, try setting the resolution of yr laptop screen to 800x600.

---

### Post by runrun on 2009-05-03
Just registered to ask the same.

I booted 9.04 on my system as a live session to test it, but I can't switch os' (coming from windows) until I can use the svideo output on my ati x1950pro - it's the main machine in our house used to stream video/media/etc to the SD tv.

On power on and during bootup (the bios post and ubuntu loading screen) I had simultaneous output on the lcd monitor and the tv (framebuffer?) - as gnome loaded the tv screen went blank and I could not see a way to get an output in ubuntu or by searching the internet.

The standard out of the box oss ati drivers seemed to be working fine, although because of this issue I did not spend a huge amount of time in the os. The desktop effects seemed smooth and glxgears gave 3000+ fps when run from terminal, and 800+ fps when run with the full screen switch (the gnome menu bar was still showing) - I have no comparison for this, 3d acceleration isn't my biggest concern, being able to display on the living room's tv is my issue.

Looking forward to a fix/solution, thanks in advance!

edit: xrandr command showed no svideo output, just the two dvi ports (one occupied) and kicked back an error saying the same when running the examples in previous posts in this thread. Will happily provide more info if its required/helps.

---

### Post by nibbana84 on 2009-05-04
> **runrun said:**
> Just registered to ask the same.

I booted 9.04 on my system as a live session to test it, but I can't switch os' (coming from windows) until I can use the svideo output on my ati x1950pro - it's the main machine in our house used to stream video/media/etc to the SD tv.

On power on and during bootup (the bios post and ubuntu loading screen) I had simultaneous output on the lcd monitor and the tv (framebuffer?) - as gnome loaded the tv screen went blank and I could not see a way to get an output in ubuntu or by searching the internet.

The standard out of the box oss ati drivers seemed to be working fine, although because of this issue I did not spend a huge amount of time in the os. The desktop effects seemed smooth and glxgears gave 3000+ fps when run from terminal, and 800+ fps when run with the full screen switch (the gnome menu bar was still showing) - I have no comparison for this, 3d acceleration isn't my biggest concern, being able to display on the living room's tv is my issue.

Looking forward to a fix/solution, thanks in advance!

edit: xrandr command showed no svideo output, just the two dvi ports (one occupied) and kicked back an error saying the same when running the examples in previous posts in this thread. Will happily provide more info if its required/helps.

Add into your /etc/X11/xorg.conf (into "Device" section):
```
Option "ATOMTvOut" "TRUE"

```
and restart. You should see S-video after that.

Let us know

---

### Post by runrun on 2009-05-07
Thanks for your reply, much appreciated.

I was using the livecd and was trying to avoid a full install over a working system just to test this feature, but found a spare drive and decided to try.

Adding the switch did allow my card to detect the svideo port, but unfortunately whatever I tried, I could still not get any output on the tv - and adding the switch just seemed to have negative consequences on my main lcd display.

I noticed this post a couple of days ago. It didn't work for me (I think it's a driver issue more than a user issue) and sounds like a strange 'fix', but maybe it'll help you:

[http://ubuntuforums.org/showthread.php?p=7234589&posted=1#post7234589](http://ubuntuforums.org/showthread.php?p=7234589&posted=1#post7234589)

---

### Post by gloscherrybomb on 2009-05-07
I have SVideo detected, but when I enable it my pc screen has some strange lines across it, and the TV is still blank. The only thing that makes me wish I still has FGLRX.

---

### Post by nibbana84 on 2009-05-10
Nothing yet. New Ubuntu is so cooler than previous versions, but I can't use it because of my stupid ATI ](*,)

I'm starting to think that this bug will never be fixed.

---

### Post by aaboelela on 2009-05-13
Hi,

check this:

[http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42](http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42)

To enable S-Video Out:
                              > xrandr --output S-video --set load_detection 1 
xrandr --output S-video --auto 
xrandr --output LVDS --offNow to go back to normal:
> xrandr --output LVDS --auto 
xrandr --output S-video --off Also you can create that in script files (e.g. **tvon** and **tvoff**) to make it easy, as following:

1. create **tvon** script file:
> cd /usr/bin
sudo vim tvonThen insert (type **i** to goto insert mode):
> xrandr --output S-video --set load_detection 1 
 xrandr --output S-video --auto 
 xrandr --output LVDS --offThen type **Esc** to go back to command mode, then save and exit using : x or :w then :q

2. Create **tvoff** script file:
> cd /usr/bin
sudo vim tvoffThen insert (type **i** to goto insert mode):
> xrandr --output LVDS --auto 
 xrandr --output S-video --off Then type **Esc** to go back to command mode, then save and exit using : x or :w then :q

3. Make the script files exectable:

> sudo chmod 777 tv*Now connect the S-Video to your TV, then type **tvon** to enable tv/s-video output, then later type in the command line **tvoff** to go back to normal.

---

### Post by opeter on 2009-05-14
Hello, does the TV out (s-video) on an GeForce 7300GS card work out of the box in the version of Ubuntu Linux?

Thanks for you answer.

---

### Post by nibbana84 on 2009-05-14
> **opeter said:**
> Hello, does the TV out (s-video) on an GeForce 7300GS card work out of the box in the version of Ubuntu Linux?

Thanks for you answer.

Please, let's not change the subject to the topic

---

### Post by andymion on 2009-05-15
> **aaboelela said:**
> Hi,

check this:

[http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42](http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42)

To enable S-Video Out:
                              Now to go back to normal:
Also you can create that in script files (e.g. **tvon** and **tvoff**) to make it easy, as following:

1. create **tvon** script file:
Then insert (type **i** to goto insert mode):
Then type **Esc** to go back to command mode, then save and exit using : x or :w then :q

2. Create **tvoff** script file:
Then insert (type **i** to goto insert mode):
Then type **Esc** to go back to command mode, then save and exit using : x or :w then :q

3. Make the script files exectable:

Now connect the S-Video to your TV, then type **tvon** to enable tv/s-video output, then later type in the command line **tvoff** to go back to normal.



Does anyone know if this works in Jaunty? He states in the article that he's using Gutsy. I'm not too worried about the script, I'm not using a laptop, just converging some old hardware to a tv desktop... and already reinstalling Jaunty to fix a garbled display problem I had two days ago. I don't want to go back to 8.10, I'm really digging 9.04!

I'll try it when I get home if there are no replies by then and report back!

---

### Post by nibbana84 on 2009-05-15
> **andymion said:**
> Does anyone know if this works in Jaunty? He states in the article that he's using Gutsy. I'm not too worried about the script, I'm not using a laptop, just converging some old hardware to a tv desktop... and already reinstalling Jaunty to fix a garbled display problem I had two days ago. I don't want to go back to 8.10, I'm really digging 9.04!

I'll try it when I get home if there are no replies by then and report back!

That shoud work, depending on what ATI card you have.
For example, it does not work if you have ATI X1400.

However, here you find which video cards are supported:

[http://wiki.ubuntu-it.org/Hardware/Video/Ati/Radeon](http://wiki.ubuntu-it.org/Hardware/Video/Ati/Radeon)

and here you find the official guide for ATI open driver for tv-out:

[http://wiki.x.org/wiki/radeonTV](http://wiki.x.org/wiki/radeonTV)

---

### Post by andymion on 2009-05-17
> **nibbana84 said:**
> That shoud work, depending on what ATI card you have.
For example, it does not work if you have ATI X1400.

However, here you find which video cards are supported:

[http://wiki.ubuntu-it.org/Hardware/Video/Ati/Radeon](http://wiki.ubuntu-it.org/Hardware/Video/Ati/Radeon)

and here you find the official guide for ATI open driver for tv-out:

[http://wiki.x.org/wiki/radeonTV](http://wiki.x.org/wiki/radeonTV)

Thank you so much. I had to reread your first post after you told me that. I didn't realize that you were saying it *would* work on the ones listed at the top.

Anyway, to reinforce your advice, the dynamic method on x.org worked flawlessly. The static configuration (editing xorg.conf) did not work, however. It WAS on the TV as I'd hoped, but every time I booted it started in low graphics mode. 

To get around that, I followed the advice in aaboelela's post, creating the tvon script. I then set it as a startup program. Not the most eloquent solution, but will work for what I need. I'll still look into why the xorg.conf solution doesn't work, but it's on the back burner now. 

I then had a problem with black video, but I solved that by turning off overlays in VLC, which fixed the problem in movie player as well. Now to see how it works with XBMC!

So far, so good! Thanks for your advice! :guitar:

---

### Post by landman 1560 on 2009-06-13
I am, of course, having the same issue.  I am using a Dell Inspiron E1505 w/ an ATI Mobility X1400.  I tried the above option posted by aaboelela but upon running the first line (xrandr --output S-video --set load_detection 1) I received this error:

[INDENT]X Error of failed request:  164
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  24
  Current serial number in output stream:  24
[/INDENT]

I am not good with video in linux and have no idea what this means.  Any advice would be great.

---

### Post by libertao on 2009-06-16
> **nibbana84 said:**
> That shoud work, depending on what ATI card you have.
For example, it does not work if you have ATI X1400.

However, here you find which video cards are supported:

[http://wiki.ubuntu-it.org/Hardware/Video/Ati/Radeon](http://wiki.ubuntu-it.org/Hardware/Video/Ati/Radeon)

and here you find the official guide for ATI open driver for tv-out:

[http://wiki.x.org/wiki/radeonTV](http://wiki.x.org/wiki/radeonTV)

So...any idea what to do if I **do** have an X1400?

---

### Post by Nerdknight on 2009-06-17
I have an ATI Mobility Radeon x700, my S-video output is not detected. 
With > Option "ATOMTvOut" "TRUE" the s-video output is detected but the image on TV is dark and reddish (maybe that's because that option is not for the x700 :-|).
Anyone knows if the x700 s-video output is supported?

---

### Post by nibbana84 on 2009-06-24
> **libertao said:**
> So...any idea what to do if I **do** have an X1400?

If you do have an X1400, you have 3 options:

- wait for an open driver without that bug (probably it won't happen)

- wait for a proprietary driver (when that will happen, it will be probably too late)

- install a previous version of linux so that you can use older versions of the proprietary driver

---

### Post by geordie on 2009-07-05
Hi,

check this:

[http://mfbernardes.com/drupal/conten...y-thinkpad-t42114](http://mfbernardes.com/drupal/conten...y-thinkpad-t42114)

To enable S-Video Out:
Quote:
xrandr --output S-video --set load_detection 1
xrandr --output S-video --auto
xrandr --output LVDS --off
Now to go back to normal:
Quote:
xrandr --output LVDS --auto
xrandr --output S-video --off
Also you can create that in script files (e.g. tvon and tvoff) to make it easy, as following:

1. create tvon script file:
Quote:
cd /usr/bin
sudo vim tvon
Then insert (type i to goto insert mode):
Quote:
xrandr --output S-video --set load_detection 1
xrandr --output S-video --auto
xrandr --output LVDS --off
Then type Esc to go back to command mode, then save and exit using : x or :w then :q

2. Create tvoff script file:
Quote:
cd /usr/bin
sudo vim tvoff
Then insert (type i to goto insert mode):
Quote:
xrandr --output LVDS --auto
xrandr --output S-video --off
Then type Esc to go back to command mode, then save and exit using : x or :w then :q

3. Make the script files exectable:

Quote:
sudo chmod 777 tv*
Now connect the S-Video to your TV, then type tvon to enable tv/s-video output, then later type in the command line tvoff to go back to normal.


This Worked For Me. Thanks! A Real Help!

---

### Post by dongalindo_86 on 2009-07-10
I'm using an ispiron e1505 with an ATI Technologies Inc M52 [Mobility Radeon X1300], and like all of you guys, I'm having the same issue, "No s-video out on jaunty jackelope" this really sucks, cause it's the first time i'm using ubuntu and for most of the things i've tried doing, i've been able to, by reading these forums,

but for this case i haven't found a solution, and i'm a noob on linux so :S please help me if you can :)   ty   


and i have already tried
******************************************************
The procedure should be (quoting [http://www.x.org/wiki/radeonTV):](http://www.x.org/wiki/radeonTV):)

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xrandr --output S-video --set tv_standard ntsc

and in case S-video is not recognized, adding in xorg.conf 
Option "ATOMTvOut" "TRUE" 
*******************************************************


and it gives me this:
*******************************************************
alex@ubuntu:~$ xrandr --output S-video --set tv_standard ntsc
X Error of failed request:  164
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  24
  Current serial number in output stream:  24
******************************************************

---

### Post by dE_logics on 2009-07-10
> 9500 9550 9600 9700 9800 X300 X550 X600 X700 X800 X850 X1050 X1300 X1550 X1600 X1650 X1800 X1900 Xpress X1200 X1250 X2100 

Now where's x1270...DAMN I hate Dell!

They stole that chip from ATI's factory without realizing it was in its beta phase and later coined x1250...after modifications!...as a result no one knows about that crap!

---

### Post by brookie on 2009-07-11
Sorry, I didn't read the whole post but I'll show you my xorg.conf file. Remember to change your virtual screen to match your dual screen sizes. Also, look at my device section; this option finally made svideo out work: 
 
Option          "TVDACLoadDetect"       "TRUE"


---------------------------
Section "Monitor"
	Identifier      "laptop"
EndSection

Section "Monitor"
	Identifier	"SONY"
EndSection

Section "Screen"
	Identifier      "Default Screen"
	Monitor         "laptop"
	Device          "Radeon 9000"
	DefaultDepth    24
	SubSection "Display"
		Depth       24
		Modes       "1400x1050" "1280x1024" "1280x960" "1360x768" "1152x864" "1024x768" "800x600" "640x480"
		Virtual	3080 1063
	EndSubSection
EndSection

Section "Device"
	Identifier      "Radeon 9000"
	Driver          "ati"
	BusID           "PCI:1:0:0"
	Option          "monitor-LVDS"          "laptop"
	Option          "TVDACLoadDetect"       "TRUE"
	Option          "TVStandard"            "ntsc"
	Option          "monitor-S-video"       "SONY"
EndSection

--------------------------------

Please back up your xorg.conf file before making any changes. Also, please don't just copy and paste this entire code from my xorg.conf file into yours, because it's specific to my Inspiron 600m laptop. 

Hope this helps. 
brook

---

### Post by JohnnyRogers on 2009-07-11
I had this problem myself, I have one laptop that is dedicated to outputting to the TV so this issue was critical. No matter what I tried it wouldn't consistently output on startup (scripts would work after the third or fourth time I ran it), and the picture was crap (very dark with some bright blowout spots).

What fixed it? Installing Ubuntu 8.04. Now it runs perfectly, with a beautiful picture, better than it ever had with XP. 

Is this a problem that may get fixed for 9.10, or is this regression here to stay?

---

### Post by lvu on 2009-07-22
I have a GA-MA69GM-S2H motherboard with an AMD 690G chipset. Integrated video is Radeon Express X1250. After upgrading to Jaunty, fglrx doesn't work, of course. I'm trying to make TV Out work with open-source radeon driver. It seems to almost work, except my TV screen remains black.
I've installed all updates from [http://ppa.launchpad.net/tormodvolden](http://ppa.launchpad.net/tormodvolden), set Option "ATOMTvOut" "true" in xorg.conf, and now xrandr shows me my S-video output. Xorg starts normally, I'm able to connect to it through x11vnc. The only suspicious thing I see is that xrandr --verbose says
```

VGA-0 disconnected (normal left inverted right x axis y axis)
        ...
        Clones:     HDMI-0
        ...
S-video connected (normal left inverted right x axis y axis)
        ...
        Clones:
        ...
HDMI-0 disconnected (normal left inverted right x axis y axis)
        ...
        Clones:     VGA-0
        ...

```
no matter if I do
xrandr --verbose --output S-video --same-as VGA-0 
or any other commands. So, I think that X simply doesn't output anything to my TV. And, by the way, when I run xrandr (setting resolution or just getting info), TV screen flickers with white every time.
What do I have to do to make my TV out work?

---

### Post by Craigwell on 2009-10-04
I have been able to make this work, using the standard xrandr commands, but cannot get a resolution that will actually fit my television screen. 

xrandr in terminal reports:

Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1360 x 1200
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 310mm x 230mm
   1280x1024      60.0  
   1024x768       85.0     75.0  
   800x600        85.1     75.0  
   640x480        85.0     75.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        59.9*+
  1152x864 (0x50)   81.6MHz
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz

Does this mean I am limited to 800x600 or 1152x864 for s-video??? 

Thanks

---

### Post by snuffy47 on 2009-11-05
> To enable S-Video Out:
Quote:
xrandr --output S-video --set load_detection 1
xrandr --output S-video --auto
xrandr --output LVDS --off
Now to go back to normal:
Quote:
xrandr --output LVDS --auto
xrandr --output S-video --off
Also you can create that in script files (e.g. tvon and tvoff) to make it easy, as following:

1. create tvon script file:
Quote:
cd /usr/bin
sudo vim tvon
Then insert (type i to goto insert mode):
Quote:
xrandr --output S-video --set load_detection 1
xrandr --output S-video --auto
xrandr --output LVDS --off
Then type Esc to go back to command mode, then save and exit using : x or :w then :q

2. Create tvoff script file:
Quote:
cd /usr/bin
sudo vim tvoff
Then insert (type i to goto insert mode):
Quote:
xrandr --output LVDS --auto
xrandr --output S-video --off
Then type Esc to go back to command mode, then save and exit using : x or :w then :q

3. Make the script files exectable:

Quote:
sudo chmod 777 tv*
Now connect the S-Video to your **[COLOR=#ff0000]TV[/COLOR]**, then type tvon to enable tv/s-video output, then later type in the command line tvoff to go back to normal.


 
Just wanted to add that the above information worked with my old compac 2100 laptop with ati graphics 60mb.  When I did the grep VGA command it was Idenmtified as ATI Technologies Inc Radeon Mobility U
 
Thanks

---

### Post by AlHounos on 2009-11-05
> **landman 1560 said:**
> I am, of course, having the same issue.  I am using a Dell Inspiron E1505 w/ an ATI Mobility X1400.  I tried the above option posted by aaboelela but upon running the first line (xrandr --output S-video --set load_detection 1) I received this error:[INDENT]X Error of failed request:  164
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  24
  Current serial number in output stream:  24
[/INDENT]I am not good with video in linux and have no idea what this means.  Any advice would be great.


I've also got the same problem.  I'm using an X1250 and 9.10 karmic, which means i don't have an xorg.conf file to edit with: ```
Option "ATOMTvOut" "TRUE"
```

Can anyone help??

---

### Post by mafi127 on 2011-04-24
sry to bump old theard, but has some body found a solution to fix TV out problem? I have HP compaq 6715b laptop whit radeon x1200 video card and my s-video in tv shows only black and white. there must be some way to make it show colors:confused:

---

### Post by Clockmender on 2011-12-15
> **mafi127 said:**
> sry to bump old theard, but has some body found a solution to fix TV out problem? I have HP compaq 6715b laptop whit radeon x1200 video card and my s-video in tv shows only black and white. there must be some way to make it show colors:confused:

Hope it is not too late but all you need to do is set your telly to, for example AV4S not AV4 - this is how it works on mine (Panasonic), bear in mind that some tellys only provide the S option on some of the AV inputs, again mine only supports S-Video on AV2 and AV4 - worth a try anyway. To do this just click your telly remote on the AV option you choose twice so the S value appears. This is also true for me when I get video from my surround sound DVD player.

Cheers

Clock

---

### Post by antipanda on 2012-02-02
I noticed that in this threat the command is used like

xrandr --output S-video  --set tv_standard ntsc
but I think it should be
xrandr --output S-video --set "tv standard" ntsc
or in my case
xrandr --output S-video --set "tv standard" pal

---

