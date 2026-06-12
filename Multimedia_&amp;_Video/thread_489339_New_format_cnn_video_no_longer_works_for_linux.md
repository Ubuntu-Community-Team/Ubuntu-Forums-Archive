---
title: "New format cnn video no longer works for linux"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by sdowney717 on 2007-07-01
How do we get it working again?

Fox news needs a greasemonkey script.
perhaps this new cnn format needs one also.

---

### Post by moore.bryan on 2007-07-01
*worked fine for me... what happens when you try to watch one?*

---

### Post by sdowney717 on 2007-07-01
A black screen

other people also are having a problem see this at fedora forum
[http://forums.fedoraforum.org/forum/showthread.php?t=159601&highlight=cnn](http://forums.fedoraforum.org/forum/showthread.php?t=159601&highlight=cnn)

you actually can watch the new format at cnn?

---

### Post by jimbob on 2007-07-01
Me too - black screen ...
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by jimbob on 2007-07-01
Good news - I got it to work after using UserAgentSwitcher and telling it that I was using NetScape 4.8 on Windows XP.   It would NOT work using default or IE6.

Did not try Opera yet.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by moore.bryan on 2007-07-01
*i'm using iceweasel... maybe that's the difference.*

---

### Post by sdowney717 on 2007-07-01
I reinstalled the flash player this time using synaptic. 
I should add that flash was working before I reinstalled. But I had done it manually not thru synaptic.
And it is working in firefox with agent switcher set to default

The Iceweasel browser is interesting, does it work with Feisty?

---

### Post by moore.bryan on 2007-07-01
*yeah, but the newest version (2.0.0.4) takes some upgraded packages that debian has, but ubuntu doesn't.  took me a while to get things playing nicely.*

---

### Post by Cell0518 on 2007-07-01
Ubuntu and Kubuntu will work if you install the following extenstions:

AdBlock Plus and UserAgentSwitcher (Netscape 4.8 (vista / xp) )

ABP
[https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)

User Agent
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Make sure you set it to Netscape 4.8 Vista and enable adblock plus (with EasyList (USA) )

If you want Fox News..

Install GreaseMonkey and The FoxNews Friendly Video script

GreaseMonkey
[https://addons.mozilla.org/en-US/firefox/addon/748](https://addons.mozilla.org/en-US/firefox/addon/748)

Script
[http://userscripts.org/scripts/show/1371](http://userscripts.org/scripts/show/1371)

Remember, if you use Fox News, go back to default on User Agent or you won't be able to see the videos there.

Hope this helps everyone,

Cell0518

---

### Post by Cell0518 on 2007-07-01
Bump!

---

### Post by williamroddy on 2007-07-02
The change to Netscape on AgentSwitcher worked for news feeds. But today, CNN opened up (for free! I've been paying for it for months!) their "Live" service, and I can't get it to work.

Has anyone else experienced this, or come up with a solution.

Why does CNN work on Apple and Windows, but not on Windows? If I didn't depend on them, being disabled as I am, I'd chuck the whole of CNN because I love Ubuntu.

Thanks to all, to the best forum on the whole net!

---

### Post by jimbob on 2007-07-03
Live does not work for me either.  It comes back with a message that I need to install Turner Media Plugin or something like that.  When you were paying for it did it work on Linux?  How did you get that plugin?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by berserker on 2007-07-03
> **jimbob said:**
> Good news - I got it to work after using UserAgentSwitcher and telling it that I was using NetScape 4.8 on Windows XP.   It would NOT work using default or IE6.

I just downloaded User Agent Switcher but the Netscape option is 7.0 not 4.8.  

I had CNN videos working using the Netscape 7.0 option earlier today but now they don't (just a black screen again).

EDIT:  Got it working again.  Some tips:  Need to enable session cookies if you block cookies like I do.  I also use Flashblock and needed to add [www.cnn.com](www.cnn.com) to the white list in order for videos to play.  I don't need Adblock Plus to play the videos.

---

### Post by egon2020 on 2007-07-03
That Turner Media Plugin is an exe.  Any idea how to workaround that?  I've never even heard of a "Turner Media Plugin"

---

### Post by carney1979 on 2007-07-05
Anyone figure out a way to get the new CNN video format (or Fox for that matter) to work in Konqueror?

David

---

### Post by williamroddy on 2007-07-05
I think I've tried everything, from Konqueror to Opera to Netscape (gag) to get it to work without the agent switcher hack. That's such a pain in the butt to make happen. And no reply from CNN (three emails to them), nor from Firefox. Other groups (SUSE, Fedora) are reporting the same problem.

This is a big deal. It's the sort of thing that causes new Linux users to go screaming into the night. By the way, some of the video doesn't even work correctly on OS X.

Does this, by any chance, have anything to do with the new Microsoft sudo-flash player I think I heard about but know nothing about?

Anyhow, this is serious, because multimedia -- with the Microsoft monopoly on it -- is the biggest block to Linux going mainstream now and if the best minds were working on ANYTHING, they ought to be working on this, in my humble opinion.

I will never quit Linux (more properly, Ubuntu), but it would be nice to get more people using it. It took me seven years to get my wife to switch. She's a writer.  And now this. She doesn't want to hear explanations. She just wants to hear my promise of a miracle operating system come true.

Help!!

---

### Post by Gremlinzzz on 2007-07-05
Don't know but your not missing  much anyways  cable news is all crap .

---

### Post by williamroddy on 2007-07-05
Actually, for a former intelligence officer, I can read (and see and hear) between the line. And I have "other" sources, and read and watch many newses. I do have the same complaint you have, but I react to it differently. I want to see what "crap" the public is being led to believe. Then I can at least tell those close to me and others who are interested what is smoke-and-mirrors and what to expect. Granted, these are still only my opinions. And I could be wrong in my analysis of multi-source news. But you can tell an awful lot about how society is going to turn out by how media leads them. As it always has been, "media" IS the problem. They are not "fair and balanced," nor "keeping them honest." They are blow-dry movie-star wanna-bes who are entertainers, not news people, and they get paid proportionate to their ratings.

But, in a free society, it is better to be forewarned than to ignore the problem that is influencing our lives. Example: how many news stories to do you hear about Linux, when open source ought to win the Nobel Peace prize as an example of multi-national cooperation?

---

### Post by egon2020 on 2007-07-05
With the way Ubuntu is growing, places like CNN won't be able to ignore Linux for long. They tried to shut out Firefox, but eventually most the IE only websites went away after the user base grew. More people supported means more people to watch their advertising. I was a Microsoft Junkie, but switched to Ubuntu about two months ago and couldn't be happier, and I don't think I'm the only one. It's only a matter of time. Sucks that I can't watch CNN though.

---

### Post by carney1979 on 2007-07-06
I had success using the UserAgentSwitcher extension (Google it, it's not available on Mozilla's site).

Then I discovered just now that the video's started working without using the extension.

When you first load the page with the video, they're broken and shaky but if you hit Firefox's reload button, then they play clearly.

Hope everybody else has success now, too.

David

---

### Post by walkerk on 2007-07-06
> **Cell0518 said:**
> Ubuntu and Kubuntu will work if you install the following extenstions:

AdBlock Plus and UserAgentSwitcher (Netscape 4.8 (vista / xp) )

ABP
[https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)

User Agent
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Make sure you set it to Netscape 4.8 Vista and enable adblock plus (with EasyList (USA) )

If you want Fox News..

Install GreaseMonkey and The FoxNews Friendly Video script

GreaseMonkey
[https://addons.mozilla.org/en-US/firefox/addon/748](https://addons.mozilla.org/en-US/firefox/addon/748)

Script
[http://userscripts.org/scripts/show/1371](http://userscripts.org/scripts/show/1371)

Remember, if you use Fox News, go back to default on User Agent or you won't be able to see the videos there.

Hope this helps everyone,

Cell0518

Thanks.. this did the trick :)

---

### Post by egon2020 on 2007-07-06
That totally works with the videos. THANKS. Still no luck with the live stream though. Anybody getting it?

---

### Post by Neovos on 2007-09-26
SOO Close

I tried just for the sake of crazy to actually install Firefox and all it's plugin madness in wine and I got VERY close. Firefox and the turner media plugin installed no problem. I then installed Macromedia flash player, also no problem (tested it on a site and worked ok). I also installed windows media player 7.1 and it installed no problem. I then logged into cnn and tried it out. Well I got VERY close. It loaded the 4 channel buttons with their image previews on the right side. It was totally working, but then it said it got an error on the actual video section. So I checked the terminal and it told me:
```

err:ole:get_inproc_class_object couldn't load in-process dll L"C:\\WINDOWS\\system32\\wmp.dll"

```
and
```

err:ole:CoGetClassObject no class object {6bf52a52-394a-11d3-b153-00c04f79faa6} could be created for context 0x1

```
I have a previous Windows XP installation that I dual boot, so I just went to it, found the wmp.dll and copied into the wine system32 folder. And it fixed the first error. But now the new error is:
```

fixme:advapi:RegisterTraceGuidsW 0x12ba121e 0x131ec880 0x129cc8d8 1 0x347874 (null) (null) 0x131ec888

```
Regular videos work using Firefox in wine. Audio and video work ok so I know flash and audio is mapping ok (but then again those work in Linux Firefox also, so not much gained yet). But like I said, it loaded those 4 channels on the side with updated images on the live streams like it does, but the video just doesn't want to start. Anybody have any ideas? 

I tried also installing the firefox windows media player plugin, but that one doesn't want to install. It fails a os check (go figure) and just never starts.

---

### Post by williamroddy on 2007-09-29
Thanks for the continued creativity. It's much appreciated.

---

### Post by jlo_sandog on 2007-10-16
[http://www.linuxquestions.org/questions/linux-software-2/cnn-live-video-591293/](http://www.linuxquestions.org/questions/linux-software-2/cnn-live-video-591293/)

---

### Post by berserker on 2007-10-16
> **jlo_sandog said:**
> [http://www.linuxquestions.org/questions/linux-software-2/cnn-live-video-591293/](http://www.linuxquestions.org/questions/linux-software-2/cnn-live-video-591293/)

Thanks for the tip!  I had to add "Flip4Mac" after "Quicktime" rather than "Windows Media Player" to get CNN Live to work.

It's a matter of tricking CNN into thinking you're using Firefox on Mac with the Quicktime Flip4Mac plugin.

Here's the user agent string I'm using (in prefs.js):

```
user_pref("useragentswitcher.5.appname", "Firefox");
user_pref("useragentswitcher.5.appversion", "5.0 (Macintosh; U; PPC Mac OS X Mach-O; en) rv:1.8.1.8) Gecko/20071008 Firefox/2.0.0.8");
user_pref("useragentswitcher.5.description", "Firefox 2.0.0.8 (Mac OS X)");
user_pref("useragentswitcher.5.platform", "MacPPC");
user_pref("useragentswitcher.5.useragent", "Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-us) rv:1.8.1.8) Gecko/20071008 Firefox/2.0.0.8");
```

---

### Post by spotdog14 on 2007-10-24
> **berserker said:**
> Thanks for the tip!  I had to add "Flip4Mac" after "Quicktime" rather than "Windows Media Player" to get CNN Live to work.

It's a matter of tricking CNN into thinking you're using Firefox on Mac with the Quicktime Flip4Mac plugin.

Here's the user agent string I'm using (in prefs.js):

```
user_pref("useragentswitcher.5.appname", "Firefox");
user_pref("useragentswitcher.5.appversion", "5.0 (Macintosh; U; PPC Mac OS X Mach-O; en) rv:1.8.1.8) Gecko/20071008 Firefox/2.0.0.8");
user_pref("useragentswitcher.5.description", "Firefox 2.0.0.8 (Mac OS X)");
user_pref("useragentswitcher.5.platform", "MacPPC");
user_pref("useragentswitcher.5.useragent", "Mozilla/5.0 (Macintosh; U; PPC Mac OS X Mach-O; en-us) rv:1.8.1.8) Gecko/20071008 Firefox/2.0.0.8");
```

Im sorry, this may sound very stupid, but where is the "/mplayerplug-in/Source/plugin-setup.cpp" located at?

---

### Post by berserker on 2007-10-24
> **spotdog14 said:**
> Im sorry, this may sound very stupid, but where is the "/mplayerplug-in/Source/plugin-setup.cpp" located at?

Download the mplayerplug-in source code from [here]("http://mplayerplug-in.sourceforge.net/download.php").

Open a terminal, cd to the directory where the package is located and then
```
tar xzvf mplayerplug-in-3.45.tar.gz
cd mplayerplug-in/Source
```

The file you're seeking is there.

---

### Post by lhaeh on 2007-12-08
It seems the mplayerplug-in compilation is rather complicated. It works fine, but you have to install quite a few libraries and plugins

The mplayer official compilation instructions are here:
[http://mplayerplug-in.sourceforge.net/install.php#plugin]("http://mplayerplug-in.sourceforge.net/install.php#plugin")

This helps:
[http://ubuntuforums.org/showthread.php?t=185547]("http://ubuntuforums.org/showthread.php?t=185547")

My configure line looked like this:
```
./configure --with-gecko-sdk=/home/lhaeh/gecko-sdk --enable-gtk2 --prefix=/usr --with-mozilla-home=/usr/lib/firefox
```

Here are the packages I installed:
```

g++
g++-4.1
libc6-dev
libstdc++6-4.1-dev
linux-libc-dev
firefox-dev
gawk
gpp
libnspr4-dev
libnss3-dev
pkg-config
libglib2.0-dev
cvsnt
libpq4
odbcinst1debian1
unixodbc
libjpeg62-dev
libxpm-dev
gettext
libruby1.8
libxt-dev
x-moto
gettext
```

I installed smplayer while in the middle of this, and it installed some dependencies that mplayerplug-in may need to compile:
```
kdelibs-data
kdelibs4c2a
libarts1c2a
libatk1.0-dev
libavahi-qt3-1
libcairo2-dev
libexpat1-dev
libfontconfig1-dev
libfreetype6-dev
libgtk2.0-dev
libice-dev
libjasper1
liblua50
liblualib50
libopenexr2c2a
libpango1.0-dev
libpng12-dev
libqt3-mt
libsm-dev
libvorbisenc2
libx11-dev
libxau-dev
libxcomposite-dev
libxcursor-dev
libxdamage-dev
libxdmcp-dev
libxext-dev
libxfixes-dev
libxft-dev
libxi-dev
libxinerama-dev
libxrandr-dev
libxrender-dev
smplayer
x11proto-composite-dev
x11proto-core-dev
x11proto-damage-dev
x11proto-fixes-dev
x11proto-input-dev
x11proto-kb-dev
x11proto-randr-dev
x11proto-render-dev
x11proto-xext-dev
x11proto-xinerama-dev
xtrans-dev
zlib1g-dev
```

If it was any of these, it would be the dev ones.

---

### Post by jlo_sandog on 2008-03-07
I updated the instructions to reflect a change in Flip4Mac version.
[http://www.linuxquestions.org/questions/linux-software-2/cnn-live-video-591293/](http://www.linuxquestions.org/questions/linux-software-2/cnn-live-video-591293/)

---

### Post by leopards on 2008-04-25
Had no trouble with normal CNN videos till April 24, 2008 then they failed to load and all I got was a black screen! Today after the upgrade to Hardy I get an error message, "The video timed out attempting to play.

Please ensure that you do not have any Flash Blocking plugins active"

Have no idea what caused this!!

---

### Post by leopards on 2008-04-30
Found a fix or rather a work around! uninstalled firefox 3.0b5 and reinstalled 2.0.0.14, now everything works like it did before!! Still have no idea why!!

---

### Post by jimbob on 2008-04-30
Works just fine for me on Hardy, FF 3.0-b5.

---

### Post by leopards on 2008-04-30
Work around was not a good answer as no plug-ins could be installed properly in FF2 Found the real answer in another part of the forum! Go to the Synaptic package manager and search for flash and remove everything but these packages
libswfdec-0.6-90 (0.6.4-2)
flashplugin-nonfree (9.0.124.0ubuntu2)
ubuntu-restricted-extras (15)
   version no.s in () got rid of all other stuff and now can see CNN videos again and have my plugins and add ons!!!

---

### Post by mindracer on 2008-05-28
I have Hardy 8.04 and CNN Live video doesnt work.  They require you to install a plugin in Windows and maybe MAC.

Please use this form to let them know you miss CNN Live Video on Ubuntu/Linux:

[http://www.cnn.com/feedback/forms/form9d.html](http://www.cnn.com/feedback/forms/form9d.html)


If you have found a workaround FOR LIVE VIDEO, please let us know..

---

### Post by jimbob on 2008-05-28
> James,

As you know Live Video isn't currently available for Linux users because of the Windows Media elements.  While we don't have a specific date when it will be compatible with your platform, we will make it known of your request.

Thanks for your interests in CNN.com video content.

Sincerely,

Kyle
CNN.com Support


Just to let you know that at least CNN replies to your form and is aware of the problem.  Their promptness kind of surprised me.

---

### Post by mindracer on 2008-05-28
yes they replied pretty quickly, the more users the email them the better in the long run to get support for ubuntu.  please email them and ask nicely! :)

---

### Post by jlo_sandog on 2008-06-07
If you have found a workaround FOR LIVE VIDEO, please let us know..[/QUOTE]

If you read the previous page you will find instructions to get "Live Video" working on linux. CNN can't help you because they use windows codecs. Write them back and ask them to use open source codecs.

---

### Post by nooblot on 2008-07-04
> **mindracer said:**
> I have Hardy 8.04 and CNN Live video doesnt work.  They require you to install a plugin in Windows and maybe MAC.
Please use this form to let them know you miss CNN Live Video on Ubuntu/Linux:
[http://www.cnn.com/feedback/forms/form9d.html](http://www.cnn.com/feedback/forms/form9d.html)
If you have found a workaround FOR LIVE VIDEO, please let us know..

haha dude how many forums/threads did you post this same post in ? 
like 367 ? :lolflag:

---

### Post by nooblot on 2008-07-04
tried these but still no luck
[http://ubuntuforums.org/showpost.php?p=2974964&postcount=21](http://ubuntuforums.org/showpost.php?p=2974964&postcount=21)
[http://ubuntuforums.org/showpost.php?p=4847342&postcount=34](http://ubuntuforums.org/showpost.php?p=4847342&postcount=34)

and I'm NOT going to go thru with this:
[http://www.linuxquestions.org/questions/linux-software-2/cnn-live-video-591293/](http://www.linuxquestions.org/questions/linux-software-2/cnn-live-video-591293/)

---

