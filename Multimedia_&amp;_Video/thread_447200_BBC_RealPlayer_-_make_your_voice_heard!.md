---
title: "BBC RealPlayer - make your voice heard!"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by itsjustarumour on 2007-05-17
Greetings Ubuntonians,

It seems that many, many Ubuntu users are unable to view embedded content on the BBC web site using the RealPlayer plugin.  Some people have had success in solving this thanks to posts on these fantastic forums, but all too many have not.

It appears that the BBC recently made some changes to their site, to the detriment of Linux users. To apply pressure to get this issue fixed, please register a complaint/feedback on the BBC website at:

[http://www.bbc.co.uk/complaints/make_complaint_step1.shtml](http://www.bbc.co.uk/complaints/make_complaint_step1.shtml)

Its a quick and easy process, and should only take you a minute or two to complete.  And feel free to post any responses you get from the Beeb up here for discussion!  :-)

Thanks in advance,
itsjustarumour

(Mods - please feel free to move this post elsewhere if you feel another section would be more appropriate.  Thanks again.)

---

### Post by ubukool on 2007-05-17
Hi itsjustarumour,

I am able to watch BBC content with the mplayer plugin for firefox.  Could you please explain the nature of the changes that the BBC have made to their website to the detriment of Linux users?  It's not credible to complain if you don't know what you're complaining about!

Many thanks!

:)

---

### Post by itsjustarumour on 2007-05-17
> **ubukool said:**
> Hi itsjustarumour,

I am able to watch BBC content with the mplayer plugin for firefox.  Could you please explain the nature of the changes that the BBC have made to their website to the detriment of Linux users?  It's not credible to complain if you don't know what you're complaining about!

Many thanks!

:)

Ubucool - I'm aware that mplayer (usually) works for the BBC site, however this post is specifically not aimed at those who choose to use mplayer, but rather at those who choose (or in my case need) to use RealPlayer.

The main changes to the BBC site were made in January 2007, and from both my own experience and others I have spoken to the many more problems arose from that point - not just in Ubuntu but with openSUSE for example.  Have a search around the forums or Google and you'll see this issue coming up time and time again with lots of frustrated users on various distros.

Some details of some the changes made in January (and discussions of) can be found on the official BBC editor's blogs site here:

[http://www.bbc.co.uk/blogs/theeditors/2007/01/in_response_to_site_changes.html](http://www.bbc.co.uk/blogs/theeditors/2007/01/in_response_to_site_changes.html)

Theres a lot of talk going on at the moment, and I feel nows a really good time to make the voice of the Linux community heard to make sure we're catered for!  :-)

---

### Post by jerrylamos on 2007-05-17
Well Real Player BBC video is running right now.  What I have to do is select "launch stand alone player" which works.  

Cheers, Jerry

---

### Post by itsjustarumour on 2007-05-17
> **jerrylamos said:**
> Well Real Player BBC video is running right now.  What I have to do is select "launch stand alone player" which works.  

Cheers, Jerry

Hi Jerry,

Glad you have it working!  :-)  Although thats not going to pass the "Granny Test".  Not my Granny anyway, she doesn't know what "launch in a standalone player" means - she just wants to click on the button and it Just Works (TM), same as shes used to in those other OS's!  ;-)

---

### Post by cgbier on 2007-05-18
The only problem that I have is that the files cannot find the correct system path to the Real Player.

Does anyone know how to fix that?

---

### Post by itsjustarumour on 2007-05-23
OK, well its been a few days and I've heard back from the BBC!  A very interesting email, in which they ADMIT to some problems with Linux  :biggrin:  (I DID also mention the problems watching embedded footage, but they seem to have ignored that)

This bit made me laugh though - they also admit to problems with Windows Vista!  :lolflag:

Anyhoo, heres the text of the email I received:

> Dear Mr ######

Thank you for your e-mail.

I appreciate you are experiencing difficulty listening to BBC Radio using the Radio Player, when it supports realplayer 10.5. We have provided the following advice on our website for Linux users:

[http://www.bbc.co.uk/radio/help/linux/](http://www.bbc.co.uk/radio/help/linux/)

We realise the situation is not ideal and are also experiencing an issue with people using Windows Vista, our response to Vista users may help to highlight further the difficulty we face, with so many different operating systems:

[http://www.bbc.co.uk/radio/help/#vista](http://www.bbc.co.uk/radio/help/#vista)

In the meantime your complaint has been fully registered on our audience log. Thank you again for contacting the BBC with your views which will help us to understand the needs of our bbc.co.uk site visitors.

Regards

Tony Brown
BBC Information


So, first of all, many thanks again to Mr Brown at Auntie Beeb for taking the time tor espond to my email.

Following the link to their Linux "Help" section gives the following:

> Audio Help : Advice for Unix/Linux users

We have found that the Real Player plugin, which is used by the BBC Radio Player, may or may not function fully depending on a combination of what flavour of unix/linux you are using, which browser you are using, which version of browser you are using, and which version of GCC built the plugin during installation.

You may find that you are only able to listen to live radio using the Listen using stand-alone Real Player link.

    * You can help us improve our unix/linux advice.

Installation guide

The BBC is not responsible for any changes you may decide to make to your computer set-up. The following is intended as a guide only to help you diagnose any problem you may be having.

Many users have emailed us how they got things working on their system:

    * Many users have found that they were able to use the BBC Radio Player after installing Real Player 10.
    * The files nphelix.so and nphelix.xpt must be in the browser's plugins directory for Opera, Firefox and Mozilla
    * You may need to log out and back in again before the changes work.
    * Some users have commented that they had to install the player and plugins as root. As root, in plugins directory, make soft links to nphelix.so and nphelix.xpt ("ln -fs /opt/RealPlayer/mozilla/nphelix.so /opt/firefox/plugins/nphelix.so" . Same for nphelix.xpt). Add whichever user(s) want to listen to group "audio" in /etc/group (more secure than giving world permissions to /dev/[sound device, ex. dsp]
    * One user has said that when running on a non-root area, disabling artsd got it working
    * One user has said that using the command artsdsp /usr/bin/realplay got it working
    * One user found using the command
      ln -s /home/me/applications/RealPlayer10/realplay
      /usr/bin/realplay
      got it working
    * A user on Suse 9.1 Professional found that the most recent update (0.9.3-1.2-i586) got the plugin working.
    * A user found that making sure the 'realplay' binary is in the PATH when FireFox starts up got things working.
    * One user suggested that any Linux users having problems with the Radio Player in Firefox should try using the Konqueror browser instead (assuming Real Player for Linux is correctly installed).
    * One user reported that Totem could not play Real Player live streams at first. He ran an 'about:plugins' command in Firefox, and discovered two plugins bound to the 'audio/x-pn-realaudio-plugin' MIME type:

      Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
      File name: libtotem-complex-plugin.so
      The Totem 2.16.3 plugin handles video and audio streams.
      MIME Type: audio/x-pn-realaudio-plugin
      Description: RealAudio document
      Suffixes: rpm
      Enabled: Yes

      and

      Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
      File name: nphelix.so
      Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.2.0
      MIME Type: audio/x-pn-realaudio-plugin
      Description: RealPlayer Plugin Metafile
      Suffixes: rpm
      Enabled: Yes

      He then located libtotem-complex-plugin.so in /usr/lib/mozilla/plugins and renamed it to libtotem-complex-plugin.so.old. After restarting all Firefox instances, he ran about:plugins again and the first Totem plugin mentioned above was no longer present. The BBC Radio Player worked fine.

More help from around the web

Helix community forums:
[https://helixcommunity.org/forum/?group_id=154](https://helixcommunity.org/forum/?group_id=154)
Provides information about Real Player 8, 10 and the Helix Player.

Ubuntu community documentation:
[https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods)
Provides advice to those trying to use RealPlayer with Ubuntu 7.04.
Mozilla

For more information on plugins for Mozilla-based browsers, see [http://plugindoc.mozdev.org/linux.html#RealPlayer](http://plugindoc.mozdev.org/linux.html#RealPlayer)

You can check which plugins you have installed by going to About:Plugins, or by going to [http://wp.netscape.com/plugins/manager.html](http://wp.netscape.com/plugins/manager.html)
Opera

For more information on plugins for Opera, You can check which plugins you have installed by going to Opera:Plugins.
Opera's support site at [http://www.opera.com/support/service/plugins/index.dml?platform=linux](http://www.opera.com/support/service/plugins/index.dml?platform=linux) contains more information about plugins on Linux/Opera.

The BBC is not responsible for the content of external sites.  


As you can see, a lot of this info is quite old. It may be of help to someone though!  :-)

Anyhoo - in conclusion - the way I read the situation at present is that "officially" the BBC site requires RealPlayer 10.5, whereas the latest Linux version is only 10.0  However, I grant that some Ubuntu users have managed to get 10.0 working using workarounds.

Doesn't help the rest of us though!  :roll:

---

### Post by twistedneck on 2007-05-26
> **cgbier said:**
> The only problem that I have is that the files cannot find the correct system path to the Real Player.

Does anyone know how to fix that?

I second this!  what is the path..

---

### Post by Unicast on 2007-05-27
> **twistedneck said:**
> I second this!  what is the path..

When you click on "launch in stand alone player" choose /usr/lib/realplay-10.0.8/realplay and drop a tick in the check-box that say always use this application.

---

### Post by Trackieman on 2007-05-27
Hi folks,
I've been (somewhat reluctantly) using the closed RealPlayer for Linux on my Laptop for about a year now.
I mainly listen to BBC Radio 4,5,7, CNI Radio, DDP Hack Radio/Binrev and Slay Radio.
I've bookmarked them all and the bookmarks are stored in my home folder in the file .realplayerrc
It's a plain text hidden file, so if you can't see it in your home folder in Nautilus, press Ctrl and H
Quit RealPlayer if it's running.
Edit the file .realplayerrc in your home folder. For example /home/YOURNAME/.realplayerrc
and add the following entry's:

[favorites]
favorite_title0=Radio 1
favorite_url0=http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram
favorite_title1=Radio 2
favorite_url1=http://www.bbc.co.uk/radio2/realmedia/fmg2.ram
favorite_title2=Radio 3
favorite_url2=http://www.bbc.co.uk/radio3/ram/r3g2.ram
favorite_title3=Radio 4
favorite_url3=http://www.bbc.co.uk/radio4/realplayer/media/fmg2.ram
favorite_title4=Five Live
favorite_url4=http://www.bbc.co.uk/fivelive/live/surestream.ram
favorite_title5=Radio 7
favorite_url5=http://www.bbc.co.uk/bbc7/realplayer/dsatg2.ram
favorite_title6=CNI Radio
favorite_url6=http://209.51.162.173:9534
favorite_title7=DDP HackRadio
favorite_url7=http://www.ddphackradio.org/stream.m3u
favorite_title8=Dishnuts
favorite_url8=http://dishnuts.net/rfd1.m3u
favorite_title9=SLAY Radio
favorite_url9=http://sc.slayradio.org:8000/listen.pls
 


It works pretty well for me. My old Celeron 466MHz laptop has replaced my FM radio in the bedroom!:popcorn:


--
The links within the [favorites] are valid only at the time of posting this reply (May, 2007).
I'm so sorry if you've just searched for this article and your netbooting from your ISP/Ubuntu/Google console in 2008+ as the links are now dead.

---

### Post by pbbear on 2007-06-06
Hello justarumour
I complained to the BBC as you suggested. 
Then I read the reply they gave you, but I'm a slow understander, so I will have to keep reading it!
Thanks for your help
pbbear

---

### Post by dustfinger on 2007-06-16
I got embedded mplayer working for the BBC and this is how I did it:
Everything that I installed I did so using Synaptic Package manager:
1. install Real Player 10.0.8
2. install Mozilla-mplayer
3. install mplayer
4. install mplayer-686   (This depends on your platform)
5. install mplayer-skins
6. install w32codecs
7. install xmms-xmmplayer

Using Firefox navigate to your favorite bbc video that you so badly want to see embedded in the browser.  [Click here for bbc video links.]("http://news.bbc.co.uk/2/hi/video_and_audio/default.stm")

Now, the video will try to load using embedded mplayer and fail as I am sure you have seen many times in the past.  Right click on the video and select configure.
Make the following changes:

- Video Output: gl
- Audio Output: alsa
- Now for the strange part: **Uncheck all check boxes** and click OK.

Now try and view the video again and voila you should be able to watch the bbc embedded as intended.

dustfinger.

---

### Post by logos34 on 2007-06-16
Well, I can no longer use MediaPlayerConnectivity to view RealPlayer content--the player opens but never connects to stream...But if I click on the BBC link below to 'open in external player' or whatever it works fine.

'Greetings Ubuntonians'...reminds me of Frank Lloyd Wright's 'Usonians'.

---

### Post by dustfinger on 2007-06-16
Okay, I need to make one correction to the above instructions.  When you first click on the bbc link that I posted above, mplayer will fail to load.  Click on the "Launch in stand alone player" option and when the stand alone mplayer is launched right click in the video area and select configure.  Select the settings in my above post making certain to uncheck all of the checkboxes and then click OK. now press the Backspace button so that firefox returns to the page with the embeded video; the video should now play embeded.  You can now play all of the videos on the bbc in embeded mode until the next time you start firefox at which point you will have to follow these instructions again.

dustfinger.

---

### Post by dustfinger on 2007-06-16
This is weird.  I uninstalled realplayer and now mplayer plays the bbc while embeded without any complaints.  I still have all of the checkboxes unchecked.  Not sure what is going on here, but I can't complain.

dustfinger.

---

### Post by itsjustarumour on 2007-06-16
> **logos34 said:**
> 'Greetings Ubuntonians'...reminds me of Frank Lloyd Wright's 'Usonians'.

Thanks for that logos34, made me chuckle!  I was thinking more of "Etonians", but enjoyed the architectural reference (although I'm more of an Alvar Aalto fan)

:-)

---

### Post by johnraff on 2007-06-18
> **dustfinger said:**
> I uninstalled realplayer and now mplayer plays the bbc while embeded without any complaints.
dustfinger.Maybe realplayer is causing the trouble.

I installed the "ubuntu restricted" codec things, mplayer, the mplayer plugin for Firefox and anything I could find in Synaptic that seemed to be a codec or to do with streaming media, then had to download w32codecs from medibuntu because it didn't appear in Synaptic.

Anyway the end result seems to be that everything Just Works... :)

 (I love mplayer's minimalist approach to playing an audio stream- no window, no "visualisations" not even a terminal- just the sounds!)

**(edit 6/29)** I spoke too soon. It seems to depend on exactly *which* BBC link it is.
The other day I had to do all that stuff Dustfinger suggested (uncheck boxes) to see a Wimbledon video, and as a result real audio didn't work any more... 

I *hate* all this media stuff. :(
One day I'll be able to just click a button and listen/watch, no questions asked...
It must be so hard because there's Money involved.

---

