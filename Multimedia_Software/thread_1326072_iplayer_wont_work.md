---
title: "iplayer wont work"
date: 2009-11-14
forum: Multimedia Software
---

### Post by leg on 2009-11-14
I have recently upgraded to 9.10 and I can no longer use the bbc iplayer. I have gone through some of the mediabuntu howtos and added the repo and re-installed flash-plugin butit still won't work. Does anyone know how to get it working.

Thanks

---

### Post by Isaacgallegos on 2009-11-14
Works fine for me. 
You might be a victim of the evil pulseaudio, which they couldn't figure out how to get rid of in 9.10.

---

### Post by carina16a on 2009-11-15
I downloaded the iplayer via Opera and was able to view a streamed program from the BBC on Friday evening - a full hour of Spooks.  However, I attempted to download another program via Opera and also Firefox, but the program refused to download.  So, I can view a streamed program, but cannot download it for later viewing.  Has anyone any suggestion as to how I may achieve the download?

---

### Post by needastick on 2009-11-15
Same for me, did a clean install 9.10 yesterday, wanted to get my wife to watch strictly to show off linux, IPlayer wouldn't work would it.

I've tried all sorts today, medibuntu repos etc. but no joy. I am able to play music videos and youtube but not the BBC. I couldn't download their desktop installer either.

Everything works aok on the other OS. Would appreciate some help if anyone has fixed it.

---

### Post by alexfish on 2009-11-15
> **needastick said:**
> Same for me, did a clean install 9.10 yesterday, wanted to get my wife to watch strictly to show off linux, IPlayer wouldn't work would it.

I've tried all sorts today, medibuntu repos etc. but no joy. I am able to play music videos and youtube but not the BBC. I couldn't download their desktop installer either.

Everything works aok on the other OS. Would appreciate some help if anyone has fixed it.
Ubuntu 9.10 comes with pulse audio  some people revert back to alsa  there are links to this in the forum however  i installed pavucontrol in synaptic pkg manager  this once installed check to see if the pavdevchooser and pavumeter has installed if not install them and check to see if there are any plugins required depending on software you have installed .goto apps sounds and video click on the pulse audio device chooser the jack should appear in the top right panel click on it and select configure local sound server click your options / also check this goto   system admin users and groups click on the keys/click to make changes /enter your password click on manage groups  /go down the list and find pulse entries click on each one in turn and anclick properties /check the boxes
root and user  that will be your log in name /once done you  can see how the system is set up from that devchooser jack . the volume meter etc will show you how many channels are open  also you may need to set sound option in each program

---

### Post by needastick on 2009-11-15
I can't seem to find pulseaudio. I can see it's installed in synaptic but its not listed as an option in sounds and video, or any other dropdown. Would it have to be activated?

---

### Post by alexfish on 2009-11-15
> **needastick said:**
> I can't seem to find pulseaudio. I can see it's installed in synaptic but its not listed as an option in sounds and video, or any other dropdown. Would it have to be activated?
double check that they are installed
what do you see in sound and videos menu entries
you may have to edit the menu 
or in edit menu add new item

   launcher properties
type                     application
command             padevchooser
comment  Change PulseAudio devices and their settings

it should located in  / user/bin

if its not there then it not installed

or do filesearch  "  padevchooser"
let me know how you get on


other readings follow this useful link

[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

---

### Post by alexfish on 2009-11-15
got to synaptic in the search type in  pulse

you should see padevchooser in the list

the box will be green if its installed

if not install it

same for 

pavucontrol

pavumeter

did you do the settings in the users and groups

---

### Post by needastick on 2009-11-16
Thanks Alexfish- been to bed. 

I've done as you suggested, installed pulse audio and changed the settings in configure local server and user and groups, but still no go.

I am able to play other streams - ITV player and 4Od but not BBC and my DVD player greys out when I try playing a film.

I have installed the 64bit version of Karmic, which Ubuntu recommends, but I'm wondering if this is the issue. The BBC help site says install Adobe air but it looks a very long and complicated process to me and I'm not really convinced that this should be necessary to enable a DVD player.

I read on here somewhere that Linux just works....

---

### Post by alexfish on 2009-11-16
Hi just got out of bed . Im using 9.10 32bit / which dvd player are you using/sounds as if plugins could be missing or compatable issue /going to wiki site to check software compats will be back soon

back now 

there are articals relating the web 

links 

[http://www.webcitation.org/5kcZznLCM](http://www.webcitation.org/5kcZznLCM)
[http://en.wikipedia.org/wiki/Adobe_Flash#Video_in_web_pages](http://en.wikipedia.org/wiki/Adobe_Flash#Video_in_web_pages)
[http://www.uluga.ubuntuforums.org/showthread.php?t=1312823&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1312823&page=2)



 try this from the terminal and post the results if possible

$ aplay -l 

and

$ gedit /etc/pulse/daemon.conf

Added
 also check to see what plugins that are available in movie play
 if there is view bbc content then check it
then get get firefox to work with movieplay
 I have not tried it but worth a shot

---

### Post by needastick on 2009-11-16
Hi,
    I'm using the standard totem. There's an extra plug in on Synaptic that I've just enabled but I can't test it out at the mo as the BBC site is down for maintenance. I reckon they've been reading this thread and they're out to spite me. 

Have you had any joy Leg?

---

### Post by varangian on 2009-11-16
> **needastick said:**
> I have installed the 64bit version of Karmic, which Ubuntu recommends, but I'm wondering if this is the issue. The BBC help site says install Adobe air but it looks a very long and complicated process to me and I'm not really convinced that this should be necessary to enable a DVD player.

I think the DVD player is another issue - may need to re-install the decess lib to player encrypted DVDs for example.

Returning to the OP's iPlayer issue I've also had some fun and games that I thought I'd pass on. I installed Karmic 64 bit yesterday and started the hoop jumping to get the pain in the *** proprietary stuff working. A Google search found a suggestion that getting the plugin direct instead of from the repository was better for 64 bit users so I went [_here_]("http://get.adobe.com/flashplayer/"), grabbed the tar and installed the libflashplayer.so manually.

This got YouTube etc. working so I thought 'job done' and went to bed. But today I tried the iPlayer and although the start screens to play TV or radio looked OK (once I'd told NoScript to allow the sites) the controls were unresponsive.

A bit more Googling found a workaround as other folks had hit the same problem. Right clicking on the control (brings up the Adobe settings dialog), holding the RMB then click on the control with LMB got things going. Not very elegant though so I did some more digging around and found that I'd grabbed the 32 bit flash library. So I snagged the 64 bit version from [_here_]("http://labs.adobe.com/downloads/flashplayer10.html").

At this point I got a bit too cavalier and just closed Firefox, swapped in the new lib and restarted Firefox. As I found out from the way Firefox blew up whenever I opened the iPlayer I should really have uninstalled properly. Even swapping the 32 bit lib back didn't work until I restarted the OS. The weird thing is that although I'm still using the 32 bit the problem with the controls has now disappeared and it's all working OK now.

Can't see how what I did produced that result but as it's all working now I'll leave well alone and leave fiddling with the 64 bit plugin until another time.

---

### Post by needastick on 2009-11-16
Hi,
    Back from the other os where everything's working fine wouldn't you know. Anyway I haven't got a hardware issue. Thanks for the links, a lot of reading there, I think I shall have to take some time to digest that lot.

I did turn off visual effects and IPlayer worked but I'm sure there will be a better solution than that.

I think you're right Varangian in that the DVD problem is a separate thing although on my set up the three items seem to have some things in common. Streaming, DVD playback and compiz.

---

### Post by varangian on 2009-11-16
Re the 64 bit flash plugin Google found me [t_his link_]("http://www.khattam.info/2009/08/18/solved-flashplugin-controls-not-working-in-ubuntu-9-10-karmic-koala-alpha-4/") which refers to control problems with the 32 bit version and how the 64 bit one is rather prone to crashing. Looks as if these problems have been around since before the release. A solution is suggested but I can't say whether it works or not.

It seems that the control issue for the 32 bit is something that hits some people and not others and does, as happened to me, mysteriously disappear. A popular suggestion is that Adobe and Compiz aren't playing nice with each other so it might be worth disabling desktop effects to see if that helps.

---

### Post by leg on 2009-11-16
> **needastick said:**
> Hi,
    I'm using the standard totem. There's an extra plug in on Synaptic that I've just enabled but I can't test it out at the mo as the BBC site is down for maintenance. I reckon they've been reading this thread and they're out to spite me. 

Have you had any joy Leg?Not yet but I am going to go through this when I get home. Last time I looked I only had one answer!

---

### Post by leg on 2009-11-16
No luck yet but I have youtube working fine and I have added root and my users to the pulse and pulse-access groups. Any other ideas.

---

### Post by needastick on 2009-11-16
The sticky by ubuntu-freak at the beginning of this section seems pretty good. He is however referring to 9.04 and I'm a bit worried about applying to 9.10

He suggests purging prior to install which seems to endorse what Varangian posted. Ah well, tomorrow's another day.

---

### Post by leg on 2009-11-17
> **needastick said:**
> The sticky by ubuntu-freak at the beginning of this section seems pretty good. He is however referring to 9.04 and I'm a bit worried about applying to 9.10

He suggests purging prior to install which seems to endorse what Varangian posted. Ah well, tomorrow's another day.I worked through that before I started this thread and I am still not quite over the finish line. The useful parts of that were related to activating the repositories as the purging bit seemed to be detrimental in the end. To get youtube working again I had to install the Adobe plug in (in synaptic) instead of the one referred to in that thread. Has the situation with pulseaudio changed from 9.04? Is pulseaudio definitely why IPlayer won't work?

---

### Post by leg on 2009-11-17
Still no luck I have gone back through the sticy mentioned and I still have no IPlayer. Any ideas as to where I should look next?

[edit] seems to be a problem with firefox (I have 3.5.5) as it works fine in Epiphany.

---

### Post by varangian on 2009-11-17
> **leg said:**
> Still no luck I have gone back through the sticy mentioned and I still have no IPlayer. Any ideas as to where I should look next?

[edit] seems to be a problem with firefox (I have 3.5.5) as it works fine in Epiphany.

I speak from a position of vast ignorance but I don't think it's Firefox to blame as mine is also 3.5.5. Maybe the plugins have got a bit messed up. You might like to try:

ls -l $(locate libflashplayer.so)

which will show you where it can be found, size, whether a symbolic link and all the other useful stuff. In my case there are various versions scattered around which came as part of the restricted-extras package that installed java, codecs etc. I'm 90% certain (but I have the memory of a goldfish so don't quote me) that after doing that Flash looked like it was there but didn't work, hence my additional hoop jumping.

As I said above I went to the Adobe site and downloaded their tar.gz file, extracted the lib and (after shutting down Firefox) put it in:

/usr/lib/mozilla/plugins/libflashplayer.so

then I set up symbolic links to:

/usr/lib/firefox-addons/plugins/
/usr/lib/xulrunner-addons/plugins/

using:

ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

and likewise for the other directory.

N.B. The -f option there nukes any existing file in the directory so you'll want to preserve these first just in case. Also you need to stick a sudo in front of those or, as I usually do, give yourself a root shell with sudo -s. Suggest you also read the man pages for the commands (if you're not already familiar with them) and the 'Malicious commands' announcement as part of the necessary due diligence before you start typing like a monkey.

On my machine I've got:

-rw-r--r-- 1 root root  9560488 2009-11-16 12:28 /usr/lib/mozilla/plugins/libflashplayer.so

This is the 32 bit version and shows as Shockwave Flash 10.0 r32 when I look at the installed plugins in Firefox. Oddly the 64 bit version is exactly the same size but it is different per the md5sum. However, I'd try the 32 bit first, I know that can work whilst the 64 bit blew up Firefox big time.

Edit: Of course some of these problems might be due to the site itself. When I went to test iPlayer a couple of days back I couldn't connect, seems the servers were down. Today the site is a complete mess visually although once you've found what you're after it will play OK.

---

### Post by leg on 2009-11-18
> **varangian said:**
> ...
Thanks for taking the time varangian. I am not on my computer at the moment but I will work through your suggestions when I get home. This will be late tonight so might not get to it until tomorrow.

---

### Post by alexfish on 2009-11-19
Hi found a link which may help ?

[http://www.audiobanter.co.uk/uk-rec-audio-general-audio/7828-new-webpage-bbc-iplayer-measurements.html](http://www.audiobanter.co.uk/uk-rec-audio-general-audio/7828-new-webpage-bbc-iplayer-measurements.html)
[http://www.audiomisc.co.uk/Linux/Sound2/ListenAgain.html](http://www.audiomisc.co.uk/Linux/Sound2/ListenAgain.html)


 found two more site here
...............................................................
[http://www.k12ltsp.org/mediawiki/index.php/How_to_setup_Flash_Player_9_with_esd-pulse_audio_sound_support](http://www.k12ltsp.org/mediawiki/index.php/How_to_setup_Flash_Player_9_with_esd-pulse_audio_sound_support)

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)
.................................................................
according to the site new beta version of flashplay provides best support for pulse? 

shows as flash player 10.1 its a tar.gz file


 any one willing to take the plunge

---

### Post by alexfish on 2009-11-20
hi back again managed to get iplayer working re ubuntu9.10 pulse audio

here is a screen shot attatched

but i will have to back track for info  back soon

back now 
  
the version that worked is flash player 10 from

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

ps managed to get vlc to play dvds don't know if it will help here

[http://ubuntuforums.org/showthread.php?t=1326970](http://ubuntuforums.org/showthread.php?t=1326970)

---

### Post by Midahed on 2009-11-21
Useful thread guys!  Thanks!  I'll be trying some of this stuff myself tomorrow to see if I can fix my long-standing 'no sound on iPlayer or YouTube' problem.

Why is sound apparently such a nightmare on Ubuntu/Kubuntu?  :(

---

### Post by SillySod on 2009-11-22
I am having a similar problem with BBC I-Player.  It just shows up with a blank viewing window and the play/rewind buttons greyed out.  There is usually a little "+" symbol next to the programme information underneath which expands but this has also disappeared.

This has just happened a couple of days ago, but I haven't changed versions of Ubuntu or installed anything new, apart from any updates which might have been downloaded.

---

### Post by SillySod on 2009-11-22
I am using Firefox 3.0.15 if it helps.  I just went into the Error Console and refreshed I-Player.  I got a lot of error messages in the console, including several saying "iplayer is not defined".

Does that mean anything to anyone?

---

### Post by alexfish on 2009-11-22
Hi
did you upgrade or clean install /  there are posts about this /  i may be able help or trace the post for you

---

### Post by alexfish on 2009-11-22
> **Midahed said:**
> Useful thread guys!  Thanks!  I'll be trying some of this stuff myself tomorrow to see if I can fix my long-standing 'no sound on iPlayer or YouTube' problem.

Why is sound apparently such a nightmare on Ubuntu/Kubuntu?  :(

 the sound is not a nightmare on ubuntu/kubuntu  or any other offering which uses Linux

  it goes something like this  

   my system is an intel atom330 intel sound on board 

    however  i use a old hercules sound card which lists as CM8738

  its what you call " alsa compliant "  detects well with linux and plays 5.1 sound
 no problem

  "does not play well with windows" 

 they are still made /cheap as chips / easy to configure/ more so with pulse

  

   don't blame pulse it generally  uses  alsa for its core  

  Marker######

try this 

[I]for sound output list for your card 
from the terminal

 aplay -l

[/I][I]then check web to see if its " alsa compliant "
[/I]
[I] 
to check sound kernel

[/I][I]

modinfo soundcore[/I]


  
check your system kernel /  menu     system /admin / system monitor
   click on the tab  system  /  check that they both match 


to test the system / menu     system /admin / system testing


End Marker##################

Added 

If you have a laptop this may help

from the terminal

aplay -l



**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem] <--------This one
Subdevices: 0/1
Subdevice #0: subdevice #0


if looks something like this


try  disable the software modem in Hardware Drivers /  in System /Admin /Menu

  if problem persists

try disable the software modem in the bios

also search site with the info it gives

there is a link here for laptops with hardware problems

[http://ubuntuforums.org/showthread.php?t=361237](http://ubuntuforums.org/showthread.php?t=361237)

---

### Post by SillySod on 2009-11-22
> **alexfish said:**
> Hi
did you upgrade or clean install /  there are posts about this /  i may be able help or trace the post for you

Thanks - I upgraded to 9.04 a while back, from 8.10, but the Iplayer has been working fine until last week when the problem I mentioned earlier occurred.  I haven't done anything else apart from keep my machine up-to-date with the updates when they become available.

---

### Post by alexfish on 2009-11-22
> **SillySod said:**
> Thanks - I upgraded to 9.04 a while back, from 8.10, but the Iplayer has been working fine until last week when the problem I mentioned earlier occurred.  I haven't done anything else apart from keep my machine up-to-date with the updates when they become available.

you can try this link

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

step 6 if you have pulse

read from start 

I will keep searching

this  looks like what your looking for

**Cannot play embedded flash videos in Karmic**
[http://ubuntuforums.org/showthread.php?t=1330214&highlight=iplayer](http://ubuntuforums.org/showthread.php?t=1330214&highlight=iplayer)

different heading  ( karmic) but may help


**[SOLVED] Multiple Sound Solution (ALSA w Pulseaudio)**
[http://ubuntuforums.org/showthread.php?t=843012&highlight=play+embedded+flash](http://ubuntuforums.org/showthread.php?t=843012&highlight=play+embedded+flash)

---

### Post by alexfish on 2009-11-28
added link for alsa / sound cards /  worth looking at

[http://www.topology.org/linux/alsa.html](http://www.topology.org/linux/alsa.html)

---

### Post by SillySod on 2009-11-29
I've tried quite a few of the solutions above but nothing has helped.

I thought I would try installing a different browser to see if this made any difference.  I have installed Konqueror, and the controls have returned on the i-player as well as the little + symbol which expands to show the programme information.

So far so good, although a banner appears across the player window saying I need to install flash.  How do I do this for Konqueror?

It looks like there is a problem with Firefox, I am happy to use Konqueror for the time being if I can get flash installed, but I would still like to find out a solution for Firefox.

---

### Post by alexfish on 2009-11-29
> **SillySod said:**
> I've tried quite a few of the solutions above but nothing has helped.

I thought I would try installing a different browser to see if this made any difference.  I have installed Konqueror, and the controls have returned on the i-player as well as the little + symbol which expands to show the programme information.

So far so good, although a banner appears across the player window saying I need to install flash.  How do I do this for Konqueror?

It looks like there is a problem with Firefox, I am happy to use Konqueror for the time being if I can get flash installed, but I would still like to find out a solution for Firefox.
  sorry I am not up on  Konqueror , but I will continue  trying   for a solution

       with firefox,

back again going to do a restart with firefox 

  I am going to  blow it out including plugs etc /etc   /  get the updates / reinstall and see what happens , happy hunting with konk
     I will try this when back home  , next week

---

### Post by myklmar on 2009-11-29
Had same problem when upgraded to Karmic from Intrepid.
Found that just by switching off visual effects i.e. 'system/preferences/appearance/visual effects...set to 'none' ' BBC IPlayer TV worked fine!

---

### Post by alexfish on 2009-11-29
thanks   myklmar
                          all input welcome

alex

---

### Post by alexfish on 2009-11-29
for @sillysod
Hi
just done a run with bbci player with the live cd every thing went well 
  until found out I have insufficient band width  /  done tests through the bbc i player
  
     mobile broadband + bad weather / internet speed / 

        worth checking on wireless connections as well
      
     although I have everything working at home 

        may be for somepeople who have problems with iplayer / firefox the above might be the     best option, there are threads about this
  
    have you noted what @ myklmar has posted

     looked in repos and showed flash player 10.0.32.18-1

alex

---

### Post by alexfish on 2009-11-29
just spotted a thread RE: [B]Firefox and Opera hangs with flash(?)  worth looking at

[http://ubuntuforums.org/showthread.php?t=1173003&highlight=iplayer](http://ubuntuforums.org/showthread.php?t=1173003&highlight=iplayer)
[/B]
added
Originally Posted by psyke83  
Try disabling the apparmor profile for Firefox. I assume the same instructions for Karmic should work.

I'm not using Lucid, but I can confirm that disabling the apparmor profile seems to improve Flash performance in Firefox (equal to Epiphany) and eliminates flicker on embedded Youtube videos.

done some reading on this one .    seems  SINCE 9.10 Karmic  this function is already DISABLED

---

### Post by Janeleaper on 2009-12-03
Hi.  I started off  a new thread on this topic, and probably shouldn't have done.

I'm in Canada so I can't use the BBC iplayer for video, which is blocked outside the UK.  I use the iplayer to listen to live radio (BBC 4, BBC 7 etc) and "Listen Again" programmes.  Since upgrading to 9.10 from 9.04, the iplayer works for live radio, but not "listen again".  

I don't have any technical knowhow, so there isn't much I can do about it unless someone has a solution.  From this thread it looks as if there isn't one at the moment.

---

### Post by alexfish on 2009-12-04
> **Janeleaper said:**
> Hi.  I started off  a new thread on this topic, and probably shouldn't have done.

I'm in Canada so I can't use the BBC iplayer for video, which is blocked outside the UK.  I use the iplayer to listen to live radio (BBC 4, BBC 7 etc) and "Listen Again" programmes.  Since upgrading to 9.10 from 9.04, the iplayer works for live radio, but not "listen again".  

I don't have any technical knowhow, so there isn't much I can do about it unless someone has a solution.  From this thread it looks as if there isn't one at the moment.


there is a post on your thread

regards alexfish

---

### Post by SillySod on 2009-12-06
I don't know what I have done (probably nothing apart from keeping up-to-date with the Ubuntu updates) but I have just checked BBC I-player again today for the first time in about a week, and it is working again back to normal!

I wish I could let people know what I did to get it working again, but I really don't think I did anything!

Maybe it was just a blip!

---

### Post by alexfish on 2009-12-07
> **SillySod said:**
> I don't know what I have done (probably nothing apart from keeping up-to-date with the Ubuntu updates) but I have just checked BBC I-player again today for the first time in about a week, and it is working again back to normal!

I wish I could let people know what I did to get it working again, but I really don't think I did anything!

Maybe it was just a blip!
Hi 

great news 

perhaps You could start  a New Thread /Solved, with your above Quote

Regards

alexfish

---

### Post by brruno on 2009-12-10
I tried the player first on firefox, then chrome to no avail. Just downloaded the 64 bit version of opera 10.10 and it works on that!

---

### Post by alexfish on 2009-12-11
> **brruno said:**
> I tried the player first on firefox, then chrome to no avail. Just downloaded the 64 bit version of opera 10.10 and it works on that!

 Hi 
did some post on this one RE: streaming Buffers every few minutes

 Opera showed a Better performance than Firefox  
   
  but you can make Firefox Faster  

RE: Firefox faster
you can try here but use with CAUTION    open up in two or three pages
    
[http://www.forevergeek.com/2005/05/f...ox_slow_downs/]("http://www.forevergeek.com/2005/05/fixing_firefox_slow_downs/")

---

### Post by leg on 2009-12-14
The latest update seems to have fixed the issue for me.

---

### Post by Meilof on 2010-06-29
> **myklmar said:**
> Had same problem when upgraded to Karmic from Intrepid.
Found that just by switching off visual effects i.e. 'system/preferences/appearance/visual effects...set to 'none' ' BBC IPlayer TV worked fine!

Weirdly, this worked for me as well (running Ubuntu 9.10)!

---

