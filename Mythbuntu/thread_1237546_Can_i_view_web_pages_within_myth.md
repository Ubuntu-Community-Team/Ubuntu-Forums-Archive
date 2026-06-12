---
title: "Can i view web pages within myth?"
date: 2009-08-11
forum: Mythbuntu
---

### Post by geekyhawkes on 2009-08-11
I have found several references to mythbrowser as a plugin and configuration of mythbrowser to use firefox but i must be having a dull day.  Where do i launch mythbrowser from within the front end? 

Sorry for the dumb question, been one of those weeks!

---

### Post by SiHa on 2009-08-11
You can find Mythbrowser here:

**Information Centre > Web**

You need to pre-configure it with bookmarks via **Utilities / Setup > Setup > Info Centre Settings > Web Settings**

TBH, unless you use Myth with a keyboard (which I don't) it's not really much use as a browser, as you can simply view pre-selected pages.

I have been playing with the 'Big-Screen' version of BBC iPlayer, as an alternative to Mythvodka etc, but you still need to emulate some mouse clicks, and I've not had time. I think it's probably the way to go though.

---

### Post by geekyhawkes on 2009-08-12
YOu pretty much read my mind with what i was trying to achieve.  I use mythpywii as my primary HMI with my myth box so im guessing the big screen iplayer will still be tricky.

EDIT::: Has this been removed at 9.04?  For some reason i dont have the menu options you described above.  I also checked the plugings listed in the mythcontrolcenter and myth web isnt listed as an option.

---

### Post by SiHa on 2009-08-12
> Has this been removed at 9.04? For some reason i dont have the menu options you described above. I also checked the plugings listed in the mythcontrolcenter and myth web isnt listed as an option.  Now that you mention it, I seem to remember reading something here about that. Probably because it's pants. 

Can you install it?

> sudo apt-get install mythbrowser

If not, it should be fairly simple to either edit the xml code for the menu to launch Firefox instead. Either that or use irexec to launch it on a certain remote control button press. ```
firefox http://bbc.co.uk/iplayer/bigscreen
``` will launch firefox straight into the bigscreen page of iplayer.

Have a look[[COLOR="Blue"]_ here_[/COLOR]](http://hatherly.com/blog/?p=31), I reckon he's onto something.

Hopefully, with a few scripted mouseclicks as in the above, it could me made useable. I've stopped trying because my frontend hasn't got the grunt to upscale the window to fullscreen. I'll have a play though when I have a little time.

EDIT: I remember now, I couldn't get flash player to install, so I was forced down the firefox route anyway.

---

### Post by HW_Hack on 2009-08-12
Wow - not being able to view web content / streaming would be a big issue. I'm still configing the basic system but I will be watching this thread.

I've got a MCE remote working - and if I needed to do a bit of typing I'd setup a wireless keybd/mouse

---

### Post by geekyhawkes on 2009-08-12
Very interesting.  I will give this a go over the weekend. 

Thanks

---

### Post by SiHa on 2009-08-13
> **HW_Hack said:**
> ...if I needed to do a bit of typing I'd setup a wireless keybd/mouse.

I've been thinking that might be the simplest way to go.

---

### Post by geekyhawkes on 2009-08-14
This sort of thing does seem an easy-ish way to sort the web problem within myth;

[http://cgi.ebay.co.uk/NEW-Mini-USB-2-4G-Wireless-RF-Media-Keyboard-Trackball_W0QQitemZ400066626632QQcmdZViewItemQQptZUK_Computing_ComputerComponents_KeyboardsMice?hash=item5d25d44448&_trksid=p3286.c0.m14](http://cgi.ebay.co.uk/NEW-Mini-USB-2-4G-Wireless-RF-Media-Keyboard-Trackball_W0QQitemZ400066626632QQcmdZViewItemQQptZUK_Computing_ComputerComponents_KeyboardsMice?hash=item5d25d44448&_trksid=p3286.c0.m14)

---

### Post by HW_Hack on 2009-08-15
> **SiHa said:**
> .

I've been thinking that might be the simplest way to go.

Yeah - after some thought I can see where a traditional web approach does not mesh well with the whole 10ft GUI experience. As you need to type - google - etc.

But I would think that (as a start) you would handle web stuff much like setting up recordings. I would think most folks just want to view streaming content not actually google something or read news. So I would think that you would have a place to type in some web URLs and some search terms 

[www.comedycentral.com](www.comedycentral.com)      Jon Stewart

Then the web app just searches those sites and shows video links by date 

You then use the remote to scroll up - down - select

---

### Post by geekyhawkes on 2009-08-15
> I would think most folks just want to view streaming content not actually google something or read news. So I would think that you would have a place to type in some web URLs and some search terms

[www.comedycentral.com](www.comedycentral.com) Jon Stewart

Then the web app just searches those sites and shows video links by date

You then use the remote to scroll up - down - select

Sounds perfect to me.  Sadly i am not smart enough to help out in making this happen (but I am trying to be smarter WRT myth).

---

### Post by t3chn0b0y on 2009-08-16
I found it easier to just to add boxee for my videos sites to my myth menu..
beats all the issues..

---

### Post by SiHa on 2009-08-16
Problem is, Boxee seems a bit resource hungry. My low-powered FE really struggled with the fancy menus.

---

### Post by ahood on 2009-08-16
Because my primary use for the Mythweb plugin is to watch Hulu videos, I found the lack of working flash in the default browser of Mythweb plugin to be a hindrance.

I configured the Mythweb plugin to launch Firefox instead of the default browser application (variant of konqueror?).

I also added firefox add-ons that block ads, maximizes screen space, etc.

Because I have a large screen tv and my system isn't powerful enough for smooth playback of maximized streaming video, I also added a Firefox add-on that enables zooming of images/videos. This works okay, but I find that the zoom is not large enough. I have two options, which are to lower the resolution of Mythbuntu or install compiz-fusion and use the desktop zoom feature.

I use a RF wireless keyboard when using Firefox, that tucks inside the tv stand when not in use. In general, I find that having a keyboard available for use with Mythbuntu to be indispensable.

I can provide greater detail on how I set this up with Mythbuntu 8.04 if there is interest.

---

### Post by SiHa on 2009-08-17
> Because I have a large screen tv and my system isn't powerful enough for smooth playback of maximized streaming video, I also added a Firefox add-on that enables zooming of images/videos. This works okay, but I find that the zoom is not large enough. I have two options, which are to lower the resolution of Mythbuntu or install compiz-fusion and use the desktop zoom feature.

I have the same problem. I'd be very interested in this firefox add-on. Also, thanks for the compiz tip, I might try that as well.

Cheers,

Simon

---

### Post by geekyhawkes on 2009-08-17
I would be intersted in a few more details in how you achieved your current end state solution ahood.

Also, how do i add boxee to my front end?  I have a reasonable machine so i would like to think it could handle the boxee interface

---

### Post by ahood on 2009-08-18
Sure thing...

A. Launch a terminal and create a script file that will start Firefox in full screen mode.

sudo nano /usr/bin/firefox-wrapper

B. Edit the file by adding the following

#!/bin/sh
/usr/bin/firefox $11
exit 0

C. Close Nano and Save the file

Ctrl + X

D. Make the firefox-wrapper file executable

sudo chmod 755 /usr/bin/firefox-wrapper

E. In the Mythtv frontend, navigate to...

Home --> Setup --> Utilities/Setup --> Info Settings --> Web

For the browser launch text box, replace default text with the following line

/usr/bin/firefox-wrapper

F. The following Firefox-Addons are recommended
[**[COLOR="Blue"]Ad Block Plus[/COLOR]**]("https://addons.mozilla.org/en-US/firefox/addon/1865")
[**[COLOR="Blue"]disable menu[/COLOR]**]("https://addons.mozilla.org/en-US/firefox/addon/3300")
[**[COLOR="Blue"]Default FullZoom Level[/COLOR]**]("https://addons.mozilla.org/en-US/firefox/addon/6965") - This works best if the default page zoom level in preferences is adjusted.

I hope this helps.

If you like this solution, vote for it at [**[COLOR="Blue"]Brainstorm[/COLOR]**]("http://brainstorm.ubuntu.com/idea/19383/").

---

### Post by SiHa on 2009-08-18
> Also, how do i add boxee to my front end

Post #9 [[COLOR="Blue"]_here_[/COLOR]](http://ubuntuforums.org/showthread.php?t=954269&highlight=boxee)

Although, further down, there's a reminder that it doesn't work on a 64-bit install, which I'd forgotten.

---

### Post by geekyhawkes on 2009-08-18
Ok, it would appear i will have to wait out then as im running 9.04 64bit.

---

### Post by SiHa on 2009-08-18
Unfortunately so am I, on the system that would have the grunt to run Boxee!

---

### Post by silverdulcet on 2009-08-19
> **SiHa said:**
> Post #9 [[COLOR="Blue"]_here_[/COLOR]](http://ubuntuforums.org/showthread.php?t=954269&highlight=boxee)

Although, further down, there's a reminder that it doesn't work on a 64-bit install, which I'd forgotten.

It works perfectly fine on 64-bit. You just need some 32-bit libraries that Boxee requires. I've been running it for quite a while. See this post for a bash script that will download and install getlibs which is a handy script that will satisfy 32-bit dependencies automatically. Then install the deb file from boxee. You can rerun it periodically to upgrade boxee to the latest version. 

[http://forum.boxee.tv/showpost.php?p=59280&postcount=57]("http://forum.boxee.tv/showpost.php?p=59280&postcount=57")

When saving this script, pay attention to the line breaks or it will not run correctly. Also, if you are not running Jaunty(9.04) change all references within the script to "jaunty" to whatever version of Ubuntu/Mythbuntu you are running (e.g. "intrepid" for 8.10)

---

### Post by SiHa on 2009-08-19
Ahood, thanks. I tried the above, but my FE still hasn't got the balls, it seems to upscale the video. At anything other than 100% zoom, the video stutters badly.

Guess I'll just have to wait until 0.22, and the Zotac Ion mobo that I'm going to treat myself to.

---

### Post by silverdulcet on 2009-08-19
> **SiHa said:**
> Ahood, thanks. I tried the above, but my FE still hasn't got the balls, it seems to upscale the video. At anything other than 100% zoom, the video stutters badly.

Guess I'll just have to wait until 0.22, and the Zotac Ion mobo that I'm going to treat myself to.

I wouldn't get my hopes up about streaming flash video performance with the Zotac Ion board. Depending on the quality of the streaming video the Atom dual core processor still struggles a bit with flash video since as of yet it is not accelerated by the graphics hardware. Unless/Until Adobe comes out with a version of flash that can use vdpau then you will most likely be disappointed. This is from the information I've read from people who have tested the boards. :(

---

### Post by SiHa on 2009-08-19
Ah well, I had wondered about flash acceleration. Thanks for clearing that up anyway. I'd hoped the Atom would be up to the task more than my old P4, whatever.
My main reason for the Ion is so I can have a nice quiet frontend and use VDPAU to play HD, (DVB-S2) the rest would just be a nice extra.  Perhaps they'll have a more gutsy processor by the time I get round to it - Christmas / New Year.

---

