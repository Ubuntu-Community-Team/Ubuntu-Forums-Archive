---
title: "To any helpful existing Ubuntu user: Please test website with proprietary video codec"
date: 2009-10-01
forum: Multimedia Software
---

### Post by porg on 2009-10-01
Could some helpful person with a most up-to-date Ubuntu, including the most common media codecs plus web browser plugins,
please check whether s/he can see the Video Content on the following webpage properly?
Thanks!

[http://news.nana10.co.il/Category/?CategoryID=300583](http://news.nana10.co.il/Category/?CategoryID=300583)

**Technical remarks:**
In Firefox (Mac) with Firbug for code inspection, it was hard to get the exact information, as this dynamic HTML page automatically puts the "alternative (no plugin) content" into the according DOM element (id="multiplayer_15_FrameDiv"). But when I opened the page in Safari (Mac), I got at least the information, that the problematic video content seems to be of the _MIME type "application/x-ms-wmp"_.

**Why am I asking you for a favor?**
I want to take a 2nd try to migrate my girlfriend from Windows to Ubuntu.
I already tried it once in 2008, but not being able to see those Israeli video sites (with their proprietary multimedia content) was reason enough for my girlfriend to stick with Windows.
Before going through the whole installation of Ubuntu PLUS all extra media packages, I would like to read a testimony, because if it doesn't work, I will rethink her migration to Linux.

---

### Post by mimor on 2009-10-01
I know this is not what you asked for, but in FF 3.5.3with 
- adobe acrobat 8.1.0.137
- DivX Web Player 1.4.0.233
- Java(TM) 2 PSE 5.0
- Microsoft DRM 9.0.0.4503
- Mozilla Default Plug-in 1.0.0.15
- Shockwave Flash 10.0.22.87 (r22)
- Silverlight Plug-In 2.0.40115.0

On wa Windows XP machine, this site looks just fine ;)

---

### Post by porg on 2009-10-01
Dear Mimor!

My question was, and still is:
Does the website with its proprietary video codecs work on WhateverWebBrowser (Ubuntu)?

Thanks for your reply, but as you noticed yourself, your testimony is a little off the topic.
But at least, I now know, that it works on Firefox (Windows XP).

---

### Post by donato roque on 2009-10-02
I have Ubuntu 9.04 Jaunty.

Browser:  Google Chrome 4.0.213.1  -the html page is fine but you're right the site player does not support this browser

Browser:  Mozilla Firefox 3.5.3    -also html page is fine but no love there either,

My thoughts:  it seemed like the site only support windows media player,  and not even flash,  (how could anybody design this and not support flash).

---

### Post by porg on 2009-10-02
To Donato: Thanks!

Any other reports?
Especially interested in reports from users with not only the plain Ubuntu installation,
but from those who extended their system with all kind of media playback software/plugins, i.e. [mplayerplugin]("http://mplayerplug-in.sourceforge.net/") etc

Testimonies very appreciated! Thanks!

---

### Post by porg on 2009-10-13
Any further reports? Please!

---

### Post by mick222 on 2009-10-13
I have mplayer plugin and vlc plugin non of them work with this site and firefox 3.5

---

### Post by mick222 on 2009-10-13
what language is this page in? Very strange when i open the page the video appears for a fraction of a sec then stops.

---

### Post by porg on 2009-10-13
> **mick222 said:**
> what language is this page in?

This is an Israeli site (domain ending co.il) using the Hebrew language written in the Hebrew alphabet.

> **mick222 said:**
> Very strange when i open the page the video appears for a fraction of a sec then stops.

What you see "for a fraction of a sec" is just a kind of preview. I don't know how exactly it is implemented. Either displaying a  thumbnail in a standard format such as JPEG which is later, after the user event (mouseclick) replaced by the Windows Media Player content, or whether this preview is actually offered through Windows Media Player.

---

### Post by porg on 2009-10-13
Thank you for your report!
It seems that I eventually have to give up, that my girlfriend can use this site without Windows. :-(
If you nevertheless have any ideas of how playback could work, those hints would be very appreciated!!!

---

### Post by helicase on 2009-10-13
Well, I gave it a try (in Firefox) and the video didn't work for me either, but...

I had a look at the frame source (right click on the player and choose This Frame>View Frame Source) and found the URL for the video. When I opened it in a new tab the video played just fine (with the Totem browser plugin).

The URL for the (current) video is at:
[http://switch206-01.castup.net/cunet/gm.asp?ak=null&ClipMediaID=4384307&st=00:00:04.868&dr=00:47:49.131](http://switch206-01.castup.net/cunet/gm.asp?ak=null&ClipMediaID=4384307&st=00:00:04.868&dr=00:47:49.131)

Hope this helps.

---

### Post by fiklein on 2010-01-31
Have you tried the solution listed in:
[http://ubuntuforums.org/showthread.php?t=986507](http://ubuntuforums.org/showthread.php?t=986507)

I have VLC and Ubuntu-restricted-extras running in Jaunty and was able to stream another Israeli news site from the IBA following these directions. I need to listen to this so my Hebrew doesn't revert to Biblical and prayer book Hebrew when I speak it.

---

### Post by porg on 2010-02-01
Dear Fiklein!

First: Thanks for your help! Sadly, this workaround is way to complicated for my girlfriend! Too many steps!

> **http://ubuntuforums.org/showthread.php?t=986507]
Here is a complete solution:

Once for all, install vlc on your machine if not already available.

To hear and record a CastUp object:
On your browser click the link which you would like to hear/record
You get the well known Media Player message
Select the second option
SAVE the (very short) file
Display it
Grab (cut for later pasting) one of the mms: URL's shown.

Start vlc
Click File
Check (select) HTTP/HTTPS/FTP/MMS
Paste the mms: URL stored above
Check Stream/Save button if you wish to record
Click Settings
Select Play Locally and/or File
Select ASF
Next to File check box, enter any .asf file name
Click OK and again OK
You are back in the vlc control widget
Start the player , enjoy the stream.

SUMMARY: use vlc pasting the mms: URL available in the something.asp file SAVED, not played, from the failing Windows Player screen.
[/QUOTE]

I have sent an email to the Nana Support, and got a kind of semi-automated only partially appropriate reply, which was mixed English/Hebrew, even though I told them that I only speak German and English, but okay, I my girlfriend helped to translate.

[QUOTE=Nana Support via Email]
Try  using firefox after you install flip2mac(it's a program that convert from WMV to QuickTime)
you'll then see :
&#1504 said:**
> http://ubuntuforums.org/attachment.php?attachmentid=145599&stc=1&d=1265018352[/IMG]


These are my conclusions of their suggested solution:

_Mac OS X_

**FIREFOX:** Works (with some drawbacks)! Within the video area, an alternative grey screen shows up, which gives you the pure media file URL (as shown on Nana Support's screenshot) for opening in a new window, and then the QuickTime plugin loads and the WindowsMedia (flip2mac) codec handles the video, thus you properly see the video! Nevertheless, the Fullscreen option is not available here. But you can work around this on Mac OS X, simply by using the screen-zoom: Hold CTRL-key and use the scroll wheel to zoom in and out.

**SAFARI:** Fails! The grey screen does not show up. I did not look into the site's source code, but I guess you could simply also show up the grey screen here, and offer the pure media link, because then Safari also could playback through the QuickTime plugin.

_Linux / Ubuntu_

**Results unknown**, as I don't have a Ubuntu setup yet!

**Could someone please test**, whether s/he also gets this alternative grey screen (as shown in the attached and quoted screenshot from Nana Support) with the direct media link in her/his browser?

If that would work, we could even circumvent the drawback of having no fullscreen, as various of the media plugins on Linux have their built-in fullscreen option!

**Thanks!!!**


---

---

### Post by fiklein on 2010-02-06
If you have not already done so, using SYNAPTIC, install VLC and ubuntu-restricted-extras.
Open VLC (Applications ---> Sound & Video ---> VLC).

IN VLC
Press Media ---> Open Network Stream

AT THE WEBSITE YOU ARE VIEWING
In the video you are trying to access, press the Windows Media Player option. It should open another website. Copy this website URL.

IN VLC 
Paste the URL into the VLC "Address" box and choose the "Protocol" to match the website URL at the drop down menu to the right of the address.
Press "Play."
That should work.

---

### Post by fiklein on 2010-02-06
PS:  I have used this for Israel Broadcasting Authority Cast-up sites where the second choice in the blue box in English says:
"Or click here to view the content directly in you Windows Media Player." Why it says this in English when the rest of the page is in Hebrew is beyond me.
[http://www.iba.org.il/media/](http://www.iba.org.il/media/)

---

### Post by porg on 2010-02-07
> **fiklein said:**
> 
AT THE WEBSITE YOU ARE VIEWING
In the video you are trying to access, press the Windows Media Player option. It should open another website. Copy this website URL.


You write as if the Windows Media Direct Link option naturally shows up.
But this is not the case in all browsers (as this site seems to run a lot of browser specific stuff).
So please, which browser have you been running?

The issue is now almost solved!
Thanks for your help so far.

---

### Post by RudyG on 2011-07-17
I know this is an old thread, but to anyone still trying to resolve this I may have a solution.

Installing a Totem Video player does the trick. I'm running Kubuntu 11.04 so I had to install it onto my system. For Gnome users it comes preinstalled now. The package names are:
Movie Player
totem-mozilla

I tested it in Firefox and Chromium.

Rudy

---

### Post by porg on 2011-07-17
@RudyG: These are great news! I'll try that out. Maybe I can eventually migrate my GF to Ubuntu.

---

### Post by sobatsu21 on 2011-07-17
Use Opera- loads PERFECTLY especially in linux!

---

### Post by RudyG on 2011-07-17
> **porg said:**
> @RudyG: These are great news! I'll try that out. Maybe I can eventually migrate my GF to Ubuntu.
It should work since Totem supports asx streams that are specific to Micro$oft. In fact you can use the Totem player to view the streams outside of the browser the way VLC was suggested for use in previous posts of this thread. I'm doing that right now. :)
> **sobatsu21 said:**
> Use Opera- loads PERFECTLY especially in linux!That's wonderful news. I've never used Opera, in fact I'm not even sure it is free. But this sounds great.

Rudy

---

