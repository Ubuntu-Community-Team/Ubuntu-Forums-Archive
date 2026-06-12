---
title: "Problem playing videos from www.wrc.com"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by aa777888 on 2008-02-17
Hi all,

If anyone's got the time, please take a look at 

[http://www.wrc.com/jsp/index.jsp?lnk=300]("http://www.wrc.com/jsp/index.jsp?lnk=300")

and any of the videos there. They appear to be wmva streams.

Running gutsy and all is up to date. mplayer reports "stopped". totem-xine reports no wmva codec. totem-gstreamer reports data stream error. vlc plays the audio portion but not the video portion. Pretty much the same behavior either in the player itself via the convenient "media" button WRC provides or in the corresponding mozilla plug-in.

It looks to me like a missing codec. Any advice would be most appreciated.

Thanks,

aa

---

### Post by ajgreeny on 2008-02-17
Work OK for me with a fully updated gutsy also.  The videos are reported as filename.wmv&wmx, whatever that really means, when I right click in the mplayer window whilst playing.  However, they play perfectly, sound and video. I have just about every codec that it's possible to install, as far as I'm aware, and don't think I've come across something that will not play for months and months; certainly not since gutsy appeared.  Al, I can suggest is that you search harder for codecs that may be missing, though I don't honestly know what you can do to make that search easier.

---

### Post by aa777888 on 2008-02-17
Thanks for taking a look, AJ. Wish it was broken for you, too ;)

---

### Post by bubieyehyeh on 2008-03-01
> **aa777888 said:**
> 
[http://www.wrc.com/jsp/index.jsp?lnk=300]("http://www.wrc.com/jsp/index.jsp?lnk=300")
and any of the videos there. They appear to be wmva streams.

Running gutsy and all is up to date. mplayer reports "stopped". totem-xine reports no wmva codec. totem-gstreamer reports data stream error. vlc plays the audio portion but not the video portion. Pretty much the same behavior either in the player itself via the convenient "media" button WRC provides or in the corresponding mozilla plug-in.

It looks to me like a missing codec. Any advice would be most appreciated.


I had the same problem, xine, vlc and totem will not play the video streams. totem wont play them at all. vlc and xine get audio but no video. I installed the mozilla-mplayer package and remove the alternative mozilla plugins for totem/xine/vlc. I then found I needed w32codecs (which has legal issues you should be aware of), the medibuntu ones didn't work but the package at [http://debian-multimedia.org/](http://debian-multimedia.org/) stable main worked for me.

Hope that helps a fellow rally fan!

---

### Post by aa777888 on 2008-03-02
Hey Bubie, thanks, but...apparently nothing is simple for me :-(

I added the repository to my /etc/apt/sources.list file and ran apt-get with the following results

~$ sudo apt-get install debian-multimedia-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package debian-multimedia-keyring

So I'm excited, hopeful and, sadly, in need of more assistance!

Thanks,

aa

---

### Post by bubieyehyeh on 2008-03-02
> **aa777888 said:**
> Hey Bubie, thanks, but...apparently nothing is simple for me :-(

I added the repository to my /etc/apt/sources.list file and ran apt-get with the following results

~$ sudo apt-get install debian-multimedia-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package debian-multimedia-keyring


Did you do a "sudo apt-get update" before the install?

Also its worth creating a /etc/apt/preferences file to stop the new repo overriding the gutsy packages. Since the packages are some of the packages may conflct with the ubuntu packages.

My /etc/apt/preferences contains....

Package: *
Pin: release l=Unofficial Multimedia Packages
Pin-Priority: 455

Use "man apt_preferences" for more information.....
The above only installs packages from the repo if they don't exist in the ubuntu repos...

I think the FAQ on the site says download the keyring package manually and install, 
cause theirs a chicken-egg problem that you don't have the gpg key for the repo, so can't 
apt-get package.

It might be easier to just manually install the packages by just downloading 

[http://debian-multimedia.org/pool/main/d/debian-multimedia-keyring/debian-multimedia-keyring_2007.02.14_all.deb](http://debian-multimedia.org/pool/main/d/debian-multimedia-keyring/debian-multimedia-keyring_2007.02.14_all.deb)
[http://debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.1_i386.deb](http://debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.1_i386.deb)

And installing my double clicking on it natilus or using command line:
"sudo dpkg -i w32codecs_20071007-0.1_i386.deb"

Hope you get it working, I'm looking forward to watching this evenings live super-special.

---

### Post by SuperBaobab on 2008-03-02
Hello everybody,

Excuse-me for my bad english (i'm french).
I've the same problem to play videos of wrc.com. I installed the w32codecs from the .deb package of [http://debian-multimedia.org](http://debian-multimedia.org) and the keyring package.
I verified in synaptic, the packages are installed. 
I reboot my computer but this is not working, i have the same problem with all the players.:(

thk

---

### Post by bubieyehyeh on 2008-03-02
> **SuperBaobab said:**
> Hello everybody,
I've the same problem to play videos of wrc.com. I installed the w32codecs from the .deb package of [http://debian-multimedia.org](http://debian-multimedia.org) and the keyring package.
I verified in synaptic, the packages are installed. 


I've only got the video's to work in mplayer. 

You need to have the mozilla-mplayer package installed to watch the videos in firefox. Also if you have any of the other mozilla plugins like mozilla-plugin-vlc, or totem-mozilla, or gxineplugin, or xine-plugin orothers it maybe using them instead of the mplayer-plugin in firefox.

If you can't get it to work in a browser I found an alternative.

If you right click on media link under the video on the site, and then select copy link location.
Then go to shell and type 

mplayer -playlist url

replacing url with copy/paste link in " quotes. e.g

mplayer -playlist "http://broadcast.global-mix.net/?m=gmuk-n.one-tv&.wvx"

The -playlist option seems to be needed since the video play a pre-recorded logo, before playing the real stream. The -playlist option I found doesn't work with gmplayer, only the vanilla mplayer.

---

### Post by aa777888 on 2008-03-02
Bubie,

Thanks, man, you are most helpful. Now we are ALMOST there!

Did a sudo apt-get update (never understood that before but now I do)
Added a /etc/apt/preference file as you described.
Did a sudo apt-get install debian-multimedia-keyring--all OK.
Realized I didn't know what package to specify on the apt-get for the codecs so downloaded and installed them again as you described--all OK.

mplayer plug-in is my setup. It mostly just lays there and doesn't play anything. HOWEVER, while I was fooling around looking at other stuff the plug-in came alive with good video and crap audio. THAT was a breakthrough. Then it stopped working again.

No joy trying to open the stream in anything although VLC keeps changing the URL to "mms:..." and playing audio.

Finally I used command line mplayer as you described and I see this

Playing [http://o-lon-04.global-mix.net/gmuk-n.one-vod/wrc0325.wmv?request=o-lon-04-1204497703&MSWMExt=.asf](http://o-lon-04.global-mix.net/gmuk-n.one-vod/wrc0325.wmv?request=o-lon-04-1204497703&MSWMExt=.asf).
Resolving o-lon-04.global-mix.net for AF_INET6...
Couldn't resolve name for AF_INET6: o-lon-04.global-mix.net
Resolving o-lon-04.global-mix.net for AF_INET...
Connecting to server o-lon-04.global-mix.net[193.27.42.198]: 80...
Cache size set to 320 KBytes

It will repeat this over and over again until I hit ctrl-C.

Yes, I'm difficult! :-)

Thanks,

aa

---

### Post by bubieyehyeh on 2008-03-03
> **aa777888 said:**
> 
mplayer plug-in is my setup. It mostly just lays there and doesn't play anything. HOWEVER, while I was fooling around looking at other stuff the plug-in came alive with good video and crap audio. THAT was a breakthrough. Then it stopped working again.

No joy trying to open the stream in anything although VLC keeps changing the URL to "mms:..." and playing audio.

Finally I used command line mplayer as you described and I see this

Playing [http://o-lon-04.global-mix.net/gmuk-n.one-vod/wrc0325.wmv?request=o-lon-04-1204497703&MSWMExt=.asf](http://o-lon-04.global-mix.net/gmuk-n.one-vod/wrc0325.wmv?request=o-lon-04-1204497703&MSWMExt=.asf).
Resolving o-lon-04.global-mix.net for AF_INET6...
Couldn't resolve name for AF_INET6: o-lon-04.global-mix.net
Resolving o-lon-04.global-mix.net for AF_INET...
Connecting to server o-lon-04.global-mix.net[193.27.42.198]: 80...
Cache size set to 320 KBytes


The mplayer plugin does seem to be a bit flaky, it locked up firefox several times yesterday and I've seen the repeating connection issue yesterday also. I just closed down and restarted firefox to fix it.

I think the wrc.com site was a bit flaky or overloaded yesterday, since the final stage (which was supposed to be shown live) was not shown in the end.

I've tried vlc, totem and my favorite xine but only mplayer can play these video streams it seems.

Also the streams seem to play one stream then jump to another url and vlc, totem and xine don't seem to following in all cases. For listening to rally radio, in my prefered xine. I found the easiest way was to run vlc with the -vv option take a note of the last url it finds, and then added a bookmark for that url. Then I can tune into rally radio without playing all the preview streams first. The url is still valid after two weeks.

---

### Post by aa777888 on 2008-03-03
Nope, can't blame it on WRC servers. My Windows machine played everything flawlessly last night with no issues at all. Clearly I still have some problem with the configuration. :confused:

---

### Post by afternine on 2008-03-25
Hi!

I have problems playing the videos on wrc.com, too. Can anyone that has got it working post the installed packages list, so I can try to find the missing ones? Please run the following command and append the file here...

sudo dpkg --get-selections > installed_packages.txt

Hope to get this working before the rally Argentina,... 

bye

---

### Post by aa777888 on 2008-03-25
Just to add another data point, I recently did a spankin' new install off Live CD, pointed mplayer at the WRC site, let it automatically add every codec it wanted from universe, and it still didn't work. :(

aa

---

### Post by bubieyehyeh on 2008-03-25
> **afternine said:**
> Hi!

I have problems playing the videos on wrc.com, too. Can anyone that has got it working post the installed packages list, so I can try to find the missing ones? Please run the following command and append the file here...

sudo dpkg --get-selections > installed_packages.txt

Hope to get this working before the rally Argentina,... 

bye

I'm running a standard gutsy system, I only need to install one non gutsy package: w32codecs

First install mozilla-mplayer package, restart firefox and check its using mplayer plugin for non-flash video embedded in websites (can't thing of another website off-hand). You may need to remove totem-mozilla or some of the other alternative mozilla plugin packages. It won't work with wrc.com until you install the latest w32codec package, but without that you should be able to  detect if it using mplayer, right click and select configure.

Once that it working I found I need to install the 20071007 version of w32codecs I did this by getting the package from (assume you need the i386 version)

[http://debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.1_i386.deb](http://debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20071007-0.1_i386.deb)

download and dpkg -i install it or use gui installer.

Restart browser it should work.

If it doesn't try running mplayer from the command line, using instructions from my earlier post, but 
adding more and more -v options you may get some idea why it isn't working.

Hope that helps.

---

### Post by afternine on 2008-03-27
Hi!

I tried all of the suggestions, and have had partial success:
- the mozilla-mplayer plugin does not work - the plugin starts, but says "Connecting to LON....." and alternates between two servers, but does never sucessfully connect.

- the command line version works OK, all I had to add was the switch to tell it to use the current display; my command look like this:
mplayer -vo X11 -playlist "http://broadcast.global-mix.net ...."

I guess I can say that situation is not perfect, but still much better indeed ;) 

Thax for all suggestions.

Is there any other thing I can do to make the mplayer plugin work inside firefox?

What my firefox says  about:plugins is appended in the attachment.

bye

---

### Post by aa777888 on 2008-03-27
You know, this is just killing me :-(

I've tried everything including building a new machine from scratch and still get crap.

This command line:

mythtv@monolithmc:~$ mplayer -playlist "http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0345.wmv&.wvx"

Returns this nonsense:

Playing [http://o-lon-02.global-mix.net/gmuk-n.one-vod/wrc0345.wmv?request=o-lon-02-1206665076&MSWMExt=.asf](http://o-lon-02.global-mix.net/gmuk-n.one-vod/wrc0345.wmv?request=o-lon-02-1206665076&MSWMExt=.asf).
Resolving o-lon-02.global-mix.net for AF_INET6...
Couldn't resolve name for AF_INET6: o-lon-02.global-mix.net
Resolving o-lon-02.global-mix.net for AF_INET...
Connecting to server o-lon-02.global-mix.net[193.27.42.190]: 80...

Over and over again continuously.

What gives?

(Sorry for the frustration)

---

### Post by bubieyehyeh on 2008-03-28
> **afternine said:**
> Hi!

I tried all of the suggestions, and have had partial success:
- the mozilla-mplayer plugin does not work - the plugin starts, but says "Connecting to LON....." and alternates between two servers, but does never sucessfully connect.

- the command line version works OK, all I had to add was the switch to tell it to use the current display; my command look like this:
mplayer -vo X11 -playlist "http://broadcast.global-mix.net ...."

I guess I can say that situation is not perfect, but still much better indeed ;) 

Thax for all suggestions.

Is there any other thing I can do to make the mplayer plugin work inside firefox?

What my firefox says  about:plugins is appended in the attachment.

bye

Looking at your plugins list the only difference with mine is that you have libvlcplugin.so installed, which I think from memory is in mozilla-plugin-vlc. It looks like it might be taking priority over mplayer. So remove the vlc plugin and it should work. 

When I got mine fixed, it worked on the command line first, then I had to remove all the mozilla video plugins except the mplayer one for it to work in the browser.

The mplayer plugin is a bit rubbish, the volume control stay up if you click it once and it crashes a fair bit, but it possible to watch the videos.

---

### Post by bubieyehyeh on 2008-03-28
> **aa777888 said:**
> You know, this is just killing me :-(
mythtv@monolithmc:~$ mplayer -playlist "http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0345.wmv&.wvx"
(Sorry for the frustration)

I've just remember something else I did.....

Try adding the -prefer-ipv4 option to the mplayer line, if that fixes it add the following line to 
~/.mplayer/config to fix it, so you don't need it on the command line.

prefer-ipv4=1

My ADSL router doesn't like IPv6 DNS lookups, and mplayer defaults to this by default. You may have the same problem.

---

### Post by aa777888 on 2008-03-28
Bubie--making progress but still not quite there. I really, really appreciate your help.

Adding that switch now gets me this over and over again, although now it sometimes pauses and grinds away at the disk drive for a while:

Playing [http://o-lon-02.global-mix.net/gmuk-n.one-vod/wrc0345.wmv?request=o-lon-02-1206704868&MSWMExt=.asf](http://o-lon-02.global-mix.net/gmuk-n.one-vod/wrc0345.wmv?request=o-lon-02-1206704868&MSWMExt=.asf).
Resolving o-lon-02.global-mix.net for AF_INET...
Connecting to server o-lon-02.global-mix.net[193.27.42.190]: 80...

But still no play...

edited to add: I let it grind away for a while and lo and behold video started to play. This seems to prove I've got some sort of network problem on the machine and not a codec problem. Trying to play another WRC video simply had it go back into the retry forever mode again (then I left for work).

It can't be my network because my Windows machines all play the WRC stuff instantly and flawlessly so this means the problem is on the ubuntu machine somewhere. It seems if we can resolve the network connectivity issue things will be great.

BTW, the reason I want to play this on my ubuntu machine is because that is  my "media center" machine running mythtv, etc. and I'd like to enjoy watching WRC on my big screen in the family room.

Continued thanks in advance!

aa

---

### Post by afternine on 2008-03-28
Hi!

Yes, I had the mozilla-plugin-vlc installed, one I removed it, the mplayer plugin did start, but as someone said before - it just alternates between "connecting" and "buffering" and never acutally connects. So no video in browser.

However, the -prefer-ipv4 option at the command line helps the standalone player to connect more quickly and plays the video with less interruptions.

I guess it is almost usable - with a little copy/paste of link addresses ;) 

BTW - I can not believe how did Hirvonen chrash out on stage 5 while having a lead of almost a minute.... Seems like Seb is going to win again....

Bye

---

### Post by aa777888 on 2008-03-28
Turned on every verbosity I can think of and this is what I get (over and over again):

mythtv@monolithmc:~$ mplayer -msglevel all=9 -prefer-ipv4 -playlist "http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx"
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
this_opt = option: prefer-ipv4
Setting prefer-ipv4=-playlist
this_opt = option: playlist
Filename for url is now [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx)
Filename for url is now [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx)
STREAM_HTTP(1), URL: [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx)
Resolving demand.global-mix.net for AF_INET...
Connecting to server demand.global-mix.net[91.193.244.18]: 80...
Request: [GET /?o=gmuk-n.one-vod/WRC0349.wmv&.wvx HTTP/1.0
Host: demand.global-mix.net
User-Agent: MPlayer/2:1.0~rc2-0ubuntu1~ppa1
Icy-MetaData: 1
Connection: close

]
--- HTTP DEBUG HEADER --- START ---
protocol:           [HTTP/1.1]
http minor version: [1]
uri:                [(null)]
method:             [(null)]
status code:        [200]
reason phrase:      [OK]
body size:          [0]
Fields:
 0 - Connection: close
 1 - Date: Sat, 29 Mar 2008 00:08:52 GMT
 2 - Server: Microsoft-IIS/6.0
 3 - X-Powered-By: PHP/5.2.4
 4 - Expires: Mon, 26 Jul 1997 05:00:00 GMT
 5 - Last-Modified: Sat, 29 Mar 2008 00:08:52 GMT
 6 - Pragma: no-cache
 7 - Content-Type: video/x-ms-wvx
--- HTTP DEBUG HEADER --- END ---
Content-Type: [video/x-ms-wvx]
Cache size set to 320 KBytes
STREAM: [null] [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx)
STREAM: Description: http streaming
STREAM: Author: Bertrand, Albeau, Reimar Doeffinger, Arpi?
STREAM: Comment: plain http
Parsing playlist file [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx)...
Trying asx...
Detected asx format
Parsing asx file: [<ASX VERSION = "3.0">
<title>gmuk-n.one-vod</title>

<!-- ASX Playout Generator v11 26-03-2008.THN -->
<!-- WorldChannel = 1 : GeoBlocked = 0 : RefChecked = 0 : OnDemand = 1-->
<!-- Detected Location = N/A  :  Detected REF = N/A -->

<ENTRY>
<REF HREF = "http://o-lon-02.global-mix.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-02-1206749332"/>
<REF HREF = "http://o-lon-02.global-mix.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-02-1206749332"/>
</ENTRY>
<LogURL href  =  "http://logs.global-mix.net/"/>
</ASX>]
Ignoring element title
Adding file [http://o-lon-02.global-mix.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-02-1206749332](http://o-lon-02.global-mix.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-02-1206749332) to element entry
Adding element REF to entry
Adding file [http://o-lon-02.global-mix.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-02-1206749332](http://o-lon-02.global-mix.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-02-1206749332) to element entry
Adding element REF to entry
Adding element ENTRY to asx
Ignoring element LogURL
Playlist successfully parsed
Config pushed level is now 2
Config pushed level is now 3
Config pushed level is now 4
get_path('codecs.conf') -> '/home/mythtv/.mplayer/codecs.conf'
Reading /home/mythtv/.mplayer/codecs.conf: Can't open '/home/mythtv/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-runtime-cpudetection --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-arts --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-gui --enable-mencoder
CommandLine: '-msglevel' 'all=9' '-prefer-ipv4' '-playlist' 'http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx'
init_freetype
get_path('font/font.desc') -> '/home/mythtv/.mplayer/font/font.desc'
font: can't open file: /home/mythtv/.mplayer/font/font.desc
font: Reading section: [info]
font: Reading section: [files]
RAW: /usr/share/mplayer/font//iso-8859-1/arial-18/iso-8859-1-a.raw  4216 x 28, 256 colors
RAW: /usr/share/mplayer/font//iso-8859-1/arial-18/iso-8859-1-b.raw  4216 x 28, 256 colors
font: Reading section: [characters]
font: Reading section: [files]
RAW: /usr/share/mplayer/font//iso-8859-1/arial-18/osd-mplayer-a.raw  536 x 32, 256 colors
RAW: /usr/share/mplayer/font//iso-8859-1/arial-18/osd-mplayer-b.raw  536 x 32, 256 colors
font: Reading section: [characters]
font: resampling alpha by factor 0.750 (192) DONE!
font: resampling alpha by factor 0.750 (192) DONE!
Bitmap font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/mythtv/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/mythtv/.mplayer/input.conf'
Can't open input config file /home/mythtv/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not open config files /home/mythtv/.lircrc and /etc/lircrc
mplayer: No such file or directory
Failed to read LIRC config file ~/.lircrc.
get_path('wrc0349.wmv?request=o-lon-02-1206749332.conf') -> '/home/mythtv/.mplayer/wrc0349.wmv?request=o-lon-02-1206749332.conf'

[[[init getch2]]]

---

### Post by bubieyehyeh on 2008-03-29
aa777888 are you using amd64 packages, I'm using i386 ones, maybe there a bug in 64 bit version thats stop it working. Might be worth trying with i386 packages. I think that is possible on AMD64 but I not sure.

Only other thing I can think of is are you connecting through a web proxy? 

On a side note, my brother just bought a asus eeepc, it has mplayer firefox plugin pre-installed and that plays wrc radio, and just the audio of the video on the home page out of the box, but doesn't have video codec it seems.


Heres my log for same thing.....

$ mplayer -msglevel all=9 -prefer-ipv4 -playlist "http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx"
MPlayer 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm)   2800+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
this_opt = option: prefer-ipv4
Setting prefer-ipv4=-playlist
this_opt = option: playlist
Filename for url is now [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.w](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.w)
Filename for url is now [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.w](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.w)
STREAM_HTTP(1), URL: [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&)
Resolving demand.global-mix.net for AF_INET...
Connecting to server demand.global-mix.net[91.193.244.18]: 80...
Request: [GET /?o=gmuk-n.one-vod/WRC0349.wmv&.wvx HTTP/1.0
Host: demand.global-mix.net
User-Agent: MPlayer/2:1.0~rc1-0ubuntu13.2
Icy-MetaData: 1
Connection: close

]
--- HTTP DEBUG HEADER --- START ---
protocol:           [HTTP/1.1]
http minor version: [1]
uri:                [(null)]
method:             [(null)]
status code:        [200]
reason phrase:      [OK]
body size:          [0]
Fields:
 0 - Connection: close
 1 - Date: Sat, 29 Mar 2008 11:03:46 GMT
 2 - Server: Microsoft-IIS/6.0
 3 - X-Powered-By: PHP/5.2.4
 4 - Expires: Mon, 26 Jul 1997 05:00:00 GMT
 5 - Last-Modified: Sat, 29 Mar 2008 11:03:46 GMT
 6 - Pragma: no-cache
 7 - Content-Type: video/x-ms-wvx
--- HTTP DEBUG HEADER --- END ---
Content-Type: [video/x-ms-wvx]
Filename for url is now [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.w](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.w)
Filename for url is now [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.w](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.w)
STREAM_ASF, URL: [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx)
Trying ASF/HTTP...Resolving demand.global-mix.net for AF_INET...
Connecting to server demand.global-mix.net[91.193.244.18]: 80...
Request [GET /?o=gmuk-n.one-vod/WRC0349.wmv&.wvx HTTP/1.0
Accept: */*
User-Agent: NSPlayer/4.1.0.3856
Host: demand.global-mix.net:80
Pragma: xClientGUID={c77e7400-738a-11d2-9add-0020af0a3278}
Pragma: no-cache,rate=1.000000,stream-time=0,stream-offset=0:0,request-context=1
Connection: Close

]
Response [HTTP/1.1 200 OK
Connection: close
Date: Sat, 29 Mar 2008 11:03:46 GMT
Server: Microsoft-IIS/6.0
X-Powered-By: PHP/5.2.4
Expires: Mon, 26 Jul 1997 05:00:00 GMT
Last-Modified: Sat, 29 Mar 2008 11:03:46 GMT
Pragma: no-cache
Content-Type: video/x-ms-wvx

]
=====> ASF Redirector
STREAM: [null] [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx)
STREAM: Description: mms and mms over http streaming
STREAM: Author: Bertrand, Reimar Doeffinger, Albeu
STREAM: Comment: originally based on work by Majormms (is that code still there?
Parsing playlist file [http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv](http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv)
Trying asx...
Detected asx format
Parsing asx file: [<ASX VERSION = "3.0">
<title>gmuk-n.one-vod</title>

<!-- ASX Playout Generator v11 26-03-2008.THN -->
<!-- WorldChannel = 1 : GeoBlocked = 0 : RefChecked = 0 : OnDemand = 1-->
<!-- Detected Location = N/A  :  Detected REF = N/A -->

<ENTRY>
<REF HREF = "http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon
<REF HREF = "http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon
</ENTRY>
<LogURL href  =  "http://logs.wdip4u.net/"/>
</ASX>]
Ignoring element title
Adding file [http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-](http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-)
Adding element REF to entry
Adding file [http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-](http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-)
Adding element REF to entry
Adding element ENTRY to asx
Ignoring element LogURL
Playlist successfully parsed
Config pushed level is now 2
Config pushed level is now 3
Config pushed level is now 4
get_path('codecs.conf') -> '/home/pjc/.mplayer/codecs.conf'
Reading /home/pjc/.mplayer/codecs.conf: Can't open '/home/pjc/.mplayer/codecs.co
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such
Using built-in default codecs.conf.
CommandLine: '-msglevel' 'all=9' '-prefer-ipv4' '-playlist' 'http://demand.globa
init_freetype
get_path('font/font.desc') -> '/home/pjc/.mplayer/font/font.desc'
font: can't open file: /home/pjc/.mplayer/font/font.desc
font: Reading section: [info]
font: Reading section: [files]
RAW: /usr/share/mplayer/font//iso-8859-1/arial-18/iso-8859-1-a.raw  4216 x 28, 2
RAW: /usr/share/mplayer/font//iso-8859-1/arial-18/iso-8859-1-b.raw  4216 x 28, 2
font: Reading section: [characters]
font: Reading section: [files]
RAW: /usr/share/mplayer/font//iso-8859-1/arial-18/osd-mplayer-a.raw  536 x 32, 2
RAW: /usr/share/mplayer/font//iso-8859-1/arial-18/osd-mplayer-b.raw  536 x 32, 2
font: Reading section: [characters]
font: resampling alpha by factor 0.750 (192) DONE!
font: resampling alpha by factor 0.750 (192) DONE!
Bitmap font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
get_path('input.conf') -> '/home/pjc/.mplayer/input.conf'
Can't open input config file /home/pjc/.mplayer/input.conf: No such file or dire
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 67 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('wrc0349.wmv?request=o-lon-02-1206788626.conf') -> '/home/pjc/.mplayer/

[[[init getch2]]]

Playing [http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-02-1](http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o-lon-02-1)
get_path('sub/') -> '/home/pjc/.mplayer/sub/'
Filename for url is now [http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?re](http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?re)
Filename for url is now [http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?re](http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?re)
STREAM_HTTP(1), URL: [http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?reque](http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?reque)
Resolving o-lon-02.wdip4u.net for AF_INET...
Connecting to server o-lon-02.wdip4u.net[193.27.42.190]: 80...
Request: [GET /gmuk-n.one-vod/wrc0349.wmv?request=o-lon-02-1206788626 HTTP/1.0
Host: o-lon-02.wdip4u.net
User-Agent: MPlayer/2:1.0~rc1-0ubuntu13.2
Icy-MetaData: 1
Connection: close

]
--- HTTP DEBUG HEADER --- START ---
protocol:           [HTTP/1.0]
http minor version: [0]
uri:                [(null)]
method:             [(null)]
status code:        [200]
reason phrase:      [OK]
body size:          [212]
Fields:
 0 - Content-Type: video/x-ms-wvx
 1 - Cache-Control: max-age=0, no-cache
 2 - Server: Cougar/9.01.01.3862
 3 - Content-Length: 212
 4 - Date: Sat, 29 Mar 2008 11:03:36 GMT
 5 - Pragma: no-cache, xResetStrm=1
 6 - Supported: com.microsoft.wm.srvppair, com.microsoft.wm.sswitch, com.microso
--- HTTP DEBUG HEADER --- END ---
Content-Type: [video/x-ms-wvx]
Content-Length: [212]
Filename for url is now [http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?re](http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?re)
Filename for url is now [http://o-lon-02.wdip4uSTREAM_ASF](http://o-lon-02.wdip4uSTREAM_ASF), URL: [http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o](http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o)
Trying ASF/HTTP...
Resolving o-lon-02.wdip4u.net for AF_INET...
Connecting to server o-lon-02.wdip4u.net[193.27.42.190]: 80...
Request [GET /gmuk-n.one-vod/wrc0349.wmv?request=o-lon-02-1206788626 HTTP/1.0
Accept: */*
User-Agent: NSPlayer/4.1.0.3856
Host: o-lon-02.wdip4u.net:80
Pragma: xClientGUID={c77e7400-738a-11d2-9add-0020af0a3278}
Pragma: no-cache,rate=1.000000,stream-time=0,stream-offset=0:0,request-context=1
Connection: Close

]
Response [HTTP/1.0 200 OK
Content-Type: application/vnd.ms.wms-hdr.asfv1
Server: Cougar/9.01.01.3862
Content-Length: 5402
Date: Sat, 29 Mar 2008 11:03:36 GMT
Pragma: no-cache, client-id=1866112493, xResetStrm=1, features="seekable,stridab
Cache-Control: no-cache, x-wms-content-size=7931581, max-age=86399, user-public,
Last-Modified: Fri, 28 Mar 2008 20:45:47 GMT
Etag: "7931581"
Supported: com.microsoft.wm.srvppair, com.microsoft.wm.sswitch, com.microsoft.wm

$H^V^U]
=====> ASF Prerecorded
=====> ASF header chunk follows
Got chunk
Size 2 read=5340
Stream bitrate properties object
 stream count=[0x2][2]
  stream id=[0x1][1]
  max bitrate=[0xc235][49717]
  is audio stream
  stream id=[0x2][2]
  max bitrate=[0x7091d][461085]
  is video stream
Max bandwidth set to 2147483647
Resolving o-lon-02.wdip4u.net for AF_INET...
Connecting to server o-lon-02.wdip4u.net[193.27.42.190]: 80...
Request [GET /gmuk-n.one-vod/wrc0349.wmv?request=o-lon-02-1206788626 HTTP/1.0
Accept: */*.net/gmuk-n.one-vod/wrc0349.wmv?re
User-Agent: NSPlayer/4.1.0.3856
Host: o-lon-02.wdip4u.net:80
Pragma: xClientGUID={c77e7400-738a-11d2-9add-0020af0a3278}
Pragma: no-cache,rate=1.000000,stream-time=0,stream-offset=0:0,request-context=2
Pragma: xPlayStrm=1
Pragma: stream-switch-entry=ffff:1:0 ffff:2:0 
Pragma: stream-switch-count=2
Connection: Close

]
Response [HTTP/1.0 200 OK
Content-Type: application/x-mms-framed
Server: Cougar/9.01.01.3862
Date: Sat, 29 Mar 2008 11:03:36 GMT
Pragma: no-cache, client-id=585905943, xResetStrm=1, features="seekable,stridabl
Cache-Control: no-cache
Last-Modified: Sat, 29 Mar 2008 11:03:36 GMT
Supported: com.microsoft.wm.srvppair, com.microsoft.wm.sswitch, com.microsoft.wm
Connection: keep-alive

]
=====> ASF Prerecorded
Cache size set to 1555 KBytes
STREAM: [null] [http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o-l](http://o-lon-02.wdip4u.net/gmuk-n.one-vod/wrc0349.wmv?request=o-l)
STREAM: Description: mms and mms over http streaming
STREAM: Author: Bertrand, Reimar Doeffinger, Albeu
STREAM: Comment: originally based on work by Majormms (is that code still there?
=====> ASF header chunk follows
CACHE_PRE_INIT: 0 [0] 0  pre:318464  eof:0  
^MCache fill:  0.00% (0 bytes)   ^MCache fill:  2.57% (40960 bytes)

Thats where the cache start filling and playback starts.....

---

### Post by bubieyehyeh on 2008-03-29
> **afternine said:**
> Hi!
However, the -prefer-ipv4 option at the command line helps the standalone player to connect more quickly and plays the video with less interruptions.


If that helps the command line add it to the config file (see my earlier post) then mozilla mplayer plugin use same option, when you restart firefox. Might help, mine setup occassionally have the connecting, buffering issue, but clicking reload in firefox seems to fix it.

---

### Post by tzedek on 2008-03-29
This problem has plagued me since I switched from windows, and after reading this thread I was messing around with it.  I removed totem completly and mplayer is working fine on wrc.com for me

---

### Post by afternine on 2008-03-29
@bubieyehyeh

Hi, I put the -prefer-ipv4 in the config file  as soon as I saw that it helps, but unfortunately, it helps only the standalone player, the plugin still alternates between connecting and buffering.

Bye

---

### Post by aa777888 on 2008-03-30
> **bubieyehyeh said:**
> aa777888 are you using amd64 packages, I'm using i386 ones, maybe there a bug in 64 bit version thats stop it working. Might be worth trying with i386 packages. I think that is possible on AMD64 but I not sure.

Only other thing I can think of is are you connecting through a web proxy? 

On a side note, my brother just bought a asus eeepc, it has mplayer firefox plugin pre-installed and that plays wrc radio, and just the audio of the video on the home page out of the box, but doesn't have video codec it seems.


Heres my log for same thing.....

$ mplayer -msglevel all=9 -prefer-ipv4 -playlist "http://demand.global-mix.net/?o=gmuk-n.one-vod/WRC0349.wmv&.wvx"
MPlayer 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team

...rest of log deleted...



Comparing the logs and I immediately see two things: 1) you are running a different version than I and 2) my version is clearly not parsing the URLs correctly.

I am running the latest. I went into Synaptic and forced the package to match yours and viola! Success!

Playback on the command line was flawless. Playback with the plug-in is spotty. I raised the buffering level to 50% and put the prefer-ipv4=1 in the config file which improved things but there is often still a problem with audio in the plug-in.

Would you mind posting what version plug-in you are using?

Thanks!!!!!!

aa

---

### Post by bubieyehyeh on 2008-03-30
> **aa777888 said:**
> Comparing the logs and I immediately see two things: 1) you are running a different version than I and 2) my version is clearly not parsing the URLs correctly.

I am running the latest. I went into Synaptic and forced the package to match yours and viola! Success!

Playback on the command line was flawless. Playback with the plug-in is spotty. I raised the buffering level to 50% and put the prefer-ipv4=1 in the config file which improved things but there is often still a problem with audio in the plug-in.

Would you mind posting what version plug-in you are using?


Glad to hear you've had some success!

$ dpkg -l | grep mplayer
ii  mozilla-mplayer                            3.40-5ubuntu5                        MPlayer-Plugin for Mozilla
ii  mplayer                                    2:1.0~rc1-0ubuntu13.2                The Ultimate Movie Player For 
ii  mplayer-doc                                2:1.0~rc1-0ubuntu13.2                The Ultimate Movie Player For 
ii  mplayer-fonts                              3.5-2                                Fonts for mplayer
ii  mplayer-skins                              2-7                                  Skins for the Ubuntu mplayer Package

I using the normal gutsy ones, including updates and security but not bacports, w32codecs from debian-multimedia.

---

### Post by aa777888 on 2008-03-31
I changed to the version plug-in you were running but only had about 5 minutes of testing time on it.

It seems better but is hard to say.

At any rate it appears to be working as well as it is probably going to and wanted to thank everyone for there interest and assistance.

Anyone friends with the mplayer and vlc teams so that we can tell both teams that both current versions are broken (i.e. won't parse the URLs correctly)?

aa

---

### Post by bubieyehyeh on 2008-04-01
> **aa777888 said:**
> I changed to the version plug-in you were running but only had about 5 minutes of testing time on it.

It seems better but is hard to say.

At any rate it appears to be working as well as it is probably going to and wanted to thank everyone for there interest and assistance.

Anyone friends with the mplayer and vlc teams so that we can tell both teams that both current versions are broken (i.e. won't parse the URLs correctly)?

aa

Probably best to post a bug on launchpad against them.

---

