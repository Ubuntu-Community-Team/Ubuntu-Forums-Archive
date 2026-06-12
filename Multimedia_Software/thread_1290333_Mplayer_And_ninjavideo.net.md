---
title: "Mplayer And ninjavideo.net"
date: 2009-10-13
forum: Multimedia Software
---

### Post by xpoff on 2009-10-13
Hey ya'll,
Ninja video just updated there beta helper from 0.3.09 to 0.3.10.. I use this great site for watching TV.  It was working great tell the update...
It load's the mplayer and just buffer's at 0% ..nothing happens or it say's getting play list...nothing happens
I'm I missing an update with java or something??

Thanx So much 

Rock On Ubuntu

Dicker

---

### Post by Alphinor on 2009-10-13
I've had the same issue and that makes me mad!! Ninjavideo itself doesn't provide any help about it in their forum... I wish someone could figure it out because this website is awesome and that would suck if I had to go back to another OS to watch it!

Thanks!

---

### Post by vinutux on 2009-10-13
check this link helps you......

[http://forum.ninjavideo.net/index.php?topic=16912.0]("http://forum.ninjavideo.net/index.php?topic=16912.0")

---

### Post by vinutux on 2009-10-13
or use XMBC with this updated plugin [http://code.google.com/p/voinage-xbmc-plugins/downloads/detail?name=Ninja%20Video20-10-08.rar&can=2&q=]("http://code.google.com/p/voinage-xbmc-plugins/downloads/detail?name=Ninja%20Video20-10-08.rar&can=2&q=")

---

### Post by vinutux on 2009-10-13
And this post says that you need java for that [http://mydewji13.blogspot.com/2009/04/ninjavideonet-on-ubuntu-jaunty.html]("http://mydewji13.blogspot.com/2009/04/ninjavideonet-on-ubuntu-jaunty.html")

---

### Post by Alphinor on 2009-10-13
Ok, I've already followed all of the instructions in the first forum post you send us too, did work fine before the new update. But not anymore. I'm not sure about your second post, what is XMBC and the link on that page gives a broken rar file... 

And I already have Java installed, the new applet loads just fine, but the videos don't

---

### Post by vinutux on 2009-10-13
XMBC is a media center software...the above link give a plugin that helps XMBC to working that site....

**[http://xbmc.org/]("http://xbmc.org/")**

4 installing XMBC **[http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step]("http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step")**

---

### Post by xpoff on 2009-10-13
Alphinor,
You have the same problem as me,  my java's working fine but the video's won't work.
I'm looking into removing mplayer and installing a different player, worth a try 
I;m also going to look into vinutux post he just put up ..than dude
DIcker

---

### Post by Laysan_A on 2009-10-13
Yeah, I'm having the same problem. Everything worked fine before they updated the video helper. The divx mirrors still load, but many of them are down now because of the work they are doing (I assume). 

Last time I had a problem loading videos there it was the result of an Ubuntu update. Fortunately one of their Ubuntu using tech guys posted the fix in the tech forum so I was only down for part of a day. This time, with their tech forum closed and the promise to ban anyone posting a mainsite tech problem anywhere else on the board, it may be a while before any answers appear on Ninja. 

There was an update the night before the change, but I can't remember what it was. Does anyone think the Ubuntu update (it might have been a K update - I'm using Kubuntu) might be the culprit?

---

### Post by Oregontreelover on 2009-10-13
I am the having the same issues with ninjavideo. It was working until they updated their applet. I dont think it is because of a Ubuntu system update because I have not let it update in four days or so.

---

### Post by xpoff on 2009-10-13
No Luck so far,

Tried some different player's,tried to reinstall everything,and gave the XMBC player a go..It's pretty cool!  Couldn't figure how to add the ninja video plug in for it though...SO ya ahhh bummber 
Dicker

---

### Post by Laysan_A on 2009-10-13
> gave the XMBC player a go..It's pretty cool!  Couldn't figure how to add the ninja video plug in for it though...

I looked at some posts on the xmbc help site and from what little I read I gather that the ninja video plugin is no longer supported and doesn't work since ninja changed to a different protocol.

---

### Post by zieglerj on 2009-10-16
I'm having the same problem. Ninja worked before they upgraded their helper but now . . . all the mplayer plugin does is either stop at 0% buffering or 'getting playlist.'

---

### Post by edin9 on 2009-10-16
Unless your using Karmic.   ```
 sudo aptitude purge totem-mozilla && sudo aptitude install gnome-mplayer gecko-mediaplayer  
```   See if that helps :)

---

### Post by edin9 on 2009-10-16
Ok, upgrading Java fixes the problem. This doesn't happen on Windows :/

---

### Post by zieglerj on 2009-10-16
A lot of much less plesant things happen on windows though ;)

---

### Post by zieglerj on 2009-10-16
How did you go about updating java? Just reinstall?

---

### Post by Laysan_A on 2009-10-17
I have the recommended version of java installed (6-16) according to Sun's verification script, and I still cannot get the Ninja main divx links to load. They will load in windows in a virtual machine, but not in linux. The captcha works, the player resolves, press play and it tries to connect, but then it stops. It wouldn't be a problem if all the mirror links worked, but a lot of them aren't working right now either.

---

### Post by wfsswmr7285 on 2009-10-17
ditto. java uptodate and such.... the divx links are aight but why go to school if one can't make full use of his university's internet speed...

please help.

---

### Post by wfsswmr7285 on 2009-10-17
Found a fix. It's akin to using a bandage to cover a stab wound, but it works, though some of the links seem s l o w....


[http://userscripts.org/scripts/show/59984](http://userscripts.org/scripts/show/59984)


You'll need Greasemonkey.

---

### Post by lovesrugers on 2009-10-17
First post here.  

I have also been having problems using the Ninjavideo.net and the ninjavideo helper with Mplayer.  As others have stated it all started with the upgrade to the newest version .3.10.

Up until now I have been watching this thread as well as the ninjavideo forum for a solution and I finally found one.  To use it you must be using Firefox as your webbrowser and have the Greasemonkey add on installed.  Once you do that install a script called Fix Ninjavideo for Linux available Here:
[http://userscripts.org/scripts/show/59984](http://userscripts.org/scripts/show/59984)
I just did this and I am now using Ninjavideo with the helper just as before with no further changes to my system.  
Hopefully this will solve most users problems with the new helper applet.

Jerry

---

### Post by lovesrugers on 2009-10-17
> **wfsswmr7285 said:**
> Found a fix. It's akin to using a bandage to cover a stab wound, but it works, though some of the links seem s l o w....


[http://userscripts.org/scripts/show/59984](http://userscripts.org/scripts/show/59984)


You'll need Greasemonkey.
Looks like you beat me to it.  I also just noticed the link seems slower than before.

Jerry

---

### Post by shockdiode on 2009-10-17
Hey there, 

I'm the author of that greasemonkey script. Just a few informational points re: ninjavideo for anyone who cares. 

It looks like the upstream host where they store their actual videos (all of their main link videos are actually hosted on megaupload) changed what you have to do to access them. So the ninjavideo kids implemented a fix that seems to only work in some windows/IE setups. 

The greasemonkey script implements the timeout required by the upstream host and changes the source of the video to directly download it from the upstream host rather than through the helper proxy on the localhost once it gets enough info from the helper to do so. 

As far as I can tell, the speed issues on some of the download links have entirely to do with the upstream host. My guess is that they've been getting hammered as of late and that's why they implemented the changes to access the videos. Unfortunately there's nothing I can do about the speed there. 

Hopefully some find the script useful. (at least you can watch videos on ninjavideo again). 

cheers

---

### Post by lovesrugers on 2009-10-17
Thanks Shockdiode for writing the script for us.  

As far as the speed is concerned I was figuring it may just be slow because it is the middle of a Saturday.   Maybe to many people trying to download stuff at once, who knows.  At least now I have access to Ninja again and I thank you for that.

Jerry

---

### Post by Alphinor on 2009-10-17
Yay!! thanks a whole lot for the little fix!!

---

### Post by zieglerj on 2009-10-17
This works great! Thank you! :)

---

### Post by shockdiode on 2009-10-17
Sure thing. I'm glad it's working for people.

(btw "using a bandage to cover a stab wound"? lol - a bit dramatic don't you think?)

Take care

---

### Post by edin9 on 2009-10-17
> **shockdiode said:**
> Hey there, 

I'm the author of that greasemonkey script. Just a few informational points re: ninjavideo for anyone who cares. 

It looks like the upstream host where they store their actual videos (all of their main link videos are actually hosted on megaupload) changed what you have to do to access them. So the ninjavideo kids implemented a fix that seems to only work in some windows/IE setups. 

The greasemonkey script implements the timeout required by the upstream host and changes the source of the video to directly download it from the upstream host rather than through the helper proxy on the localhost once it gets enough info from the helper to do so. 

As far as I can tell, the speed issues on some of the download links have entirely to do with the upstream host. My guess is that they've been getting hammered as of late and that's why they implemented the changes to access the videos. Unfortunately there's nothing I can do about the speed there. 

Hopefully some find the script useful. (at least you can watch videos on ninjavideo again). 

cheers

  It doesn't even work that well on Windows anymore either.

---

### Post by xpoff on 2009-10-17
Just like to say thanx ,, greeesey  work's great

These forum's are awesome 

Dicker

---

### Post by wfsswmr7285 on 2009-10-18
> **shockdiode said:**
> Sure thing. I'm glad it's working for people.

(btw "using a bandage to cover a stab wound"? lol - a bit dramatic don't you think?)

Take care

Haha thanks for the great script man. A little dramatic I suppose - didn't think that the author of such a great script would grace the world of ubuntuforums with his/her presence.

Of course it would be great if ninjavideo would acknowledge the existence of linux, but until that day, I'll be using this script!

---

### Post by shockdiode on 2009-10-18
Haha, no worries. Again, you crack me up "grace with their presence" to paraprhase...


You, my friend, have a flair for the dramatic to be sure ;) It's not such a fancy script, but it does fix the issue. 

Glad it works for you as well. I wish it wasn't necessary at all though.

---

### Post by xpoff on 2009-10-18
> **xpoff said:**
> Just like to say thanx ,, greeesey  work's great

These forum's are awesome 

Dicker

I take it back for some reason it worked once... weard!
I posted a new link [http://ubuntuforums.org/showthread.php?t=1294768](http://ubuntuforums.org/showthread.php?t=1294768)  

an help would be appreciated

---

### Post by shockdiode on 2009-10-18
> **xpoff said:**
> I take it back for some reason it worked once... weard!
I posted a new link [http://ubuntuforums.org/showthread.php?t=1294768](http://ubuntuforums.org/showthread.php?t=1294768)  

an help would be appreciated

Hmm, I can't really say honestly. It seems to be working fine for me and others. Can you post a link to a video that's not working for you? 

Some steps to try/notes:

First, make sure you didn't accidentally turn off greasemonkey. 

Please note that this greasemonkey script is only helpful for the main links to the videos (the ones where you have to enter the captcha code), not the divx mirrors. Many of the divx mirrors are just screwed. 

Try logging out of your gnome/kde/whatever session and logging back in. Once in awhile the mplayer plugin just wigs out on me and this gets it back in order. (there are ways to resolve this without logging out/back in but I don't feel like typing it all up ;))

---

### Post by Laysan_A on 2009-10-18
THANKS SO MUCH Shockdiode!!!

It works like a charm.

---

### Post by xpoff on 2009-10-19
> **shockdiode said:**
> Hmm, I can't really say honestly. It seems to be working fine for me and others. Can you post a link to a video that's not working for you? 

Some steps to try/notes:

First, make sure you didn't accidentally turn off greasemonkey. 

Please note that this greasemonkey script is only helpful for the main links to the videos (the ones where you have to enter the captcha code), not the divx mirrors. Many of the divx mirrors are just screwed. 

Try logging out of your gnome/kde/whatever session and logging back in. Once in awhile the mplayer plugin just wigs out on me and this gets it back in order. (there are ways to resolve this without logging out/back in but I don't feel like typing it all up ;))



Ya I got it sorted,
It was because the mplayer stays open some how, and I had to manually close them in the monitor process selection, 
Sweet 
DIcker

---

### Post by nsac on 2009-10-23
> **shockdiode said:**
> 
The greasemonkey script implements the timeout required by the upstream host and changes the source of the video to directly download it from the upstream host rather than through the helper proxy on the localhost once it gets enough info from the helper to do so. 


Hey thanks for the fix! 

Something I've noticed this morning, if the video is not dl'ing through the helper proxy the host limits the amount you can dl. Is there a way to change it so it uses the proxy again?

---

### Post by nsac on 2009-10-23
eeep!

nevermind, it's all working. I dunno what happened this morning.

Thanks again for the fix!

---

### Post by zieglerj on 2009-10-24
This was working perfectly for me then all the sudden, an hour ago, the gecko plugin stopped loading the videos. The plugin itslef loads but there is no cacheing and it won't play. Any ideas?

---

### Post by zieglerj on 2009-10-24
I really wish these guys would get their sh** together. It's a really high quality site when it's working properly but lately . . .  

Has anyone else had problems with full screen ads that don't have the "skip this ad" button popping up during videos?

---

### Post by Oregontreelover on 2009-10-25
Check the mplayer configuration. Make sure that " Play nedia directly from site (No Caching)" is not enabled.

---

### Post by 8b1fbe046ecfe3a1f55c2eaf4f03bbc6 on 2009-11-10
I've been trying to get ninjavideo working without any luck. The best I can get mplay caching up to 18%, then stating "connecting" followed by "stopped". With the greasemonkey script installed, mplayer just crashes and shows me a white square after the countdown.

I'm using jre, mplayer and gecko mplayer. As far as I know I have all the necessary codecs installed, and I'm using ubuntu 9.10. If anyone can help me I'd really appreciate it, this is one of the last things I'm rebooting into windows for :)

---

### Post by 5ully on 2009-11-22
I am having a similar issue.  Just put 9.10 on my computer.  I've followed steps all throughout various forums and finally got the ninjavideo applet to load.

For regular links to TV shows, after I type in the code, I get the 45 second countdown.  However, at the end of the countdown when I finally get the controls to pop up on the bottom, I can hit play, and it will briefly say playing -> connecting -> cache fill 1.62% and then it will stop.

For the divx links to the shows, from what I can tell so far it won't let me stream from the browser itself, but downloading it is fine.  

Thanks for the help.

---

### Post by dolphinsonar on 2009-12-04
Subscribing, same here.  Ninjavideo must be tinkering on their side.  I am running firefox 3.5X, gecko, Sun Java 6 with Mplayer.  I pass the captcha and it showed a blank player with a white band taking up about 80% of the screen.  It would say "buffering" for a long time, then crap out.

---

### Post by zieglerj on 2009-12-12
bump

---

### Post by 8b1fbe046ecfe3a1f55c2eaf4f03bbc6 on 2009-12-16
I've actually installed the chromium browser in hopes that it might have better divx support, but I'm having the same issues - total noncompliance from totem, and mplayer caching up to 20% and then falling back to "connecting" and finally "stopped".

I'm really interested in getting this resolved, as I've just purchased a dell mini 10v with ubuntu preloaded. It's my first all-ubuntu system, and I do NOT want to have windows on there just to watch divx movies! (there's also a small sense of urgency due to the next (and final!) season of Lost being aired in February :popcorn:)

Please help guys, I've great faith in the combined genius of this forum!

 - Tom

---

### Post by myddewji13 on 2009-12-19
which version of mplayer are you using? I'm using the version from ubuntu tweaks 3rd party repos. (I had problems with the stock ubuntu one..)

try adding this ppa:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by 8b1fbe046ecfe3a1f55c2eaf4f03bbc6 on 2009-12-21
I'm having exactly the same problem with that version of mplayer :\

What intrigues me is that while everyone else has got it working with the greasemonkey script, when I try and use it, after the countdown I see a grey box - a crashed mplayer, presumably. 

Could it be a problem with firefox? I'm using 3.5.6+nobinonly-0ubuntu0.9.10.1.

I'm using mozilla-mplayer 3.55-2ubuntu1 and gnome-mplayer 0.9.8-1ubuntu2. I'm baffled.

Could it be something to do with me using a 64bit version of ubuntu?

:confused:

Thanks for taking the time to help, myddewji13.

---

### Post by JSMskater on 2009-12-22
I'm a noob so bear with me, but I just upgraded to 9.10 and wanted to watch ninjavideo on this computer since I just hooked up my desktop to the new plasma via HDMI cable... :popcorn:

I've tried updating/installing:

adoble flash
java 6 
mplayer
gnome mplayer

and I still can't get anything to show up :confused: 

I open the video helper, it doesn't seem display the "online" message, and then if I click on a video link to stream it the video player nor the typical code/authentication applet you punch in show up. Anybody know how the heck you can watch ninja? I'm sure somebody is doin it...

---

### Post by EvilGnome on 2009-12-25
I'm watching successfully on arch linux with:

[http://userscripts.org/scripts/show/59984](http://userscripts.org/scripts/show/59984)
jre 6u17
flashplugin 10.0.42.34
mplayer-plugin 3.55
chromium 4.0.249.43

This setup was working fine when I used firefox as well. I'm pretty sure the important parts are just to use the greasemonkey script and the old, dead mplayer-plugin.

If you want to get gecko-mediaplayer working with ninjavideo and firefox, help out here: [http://code.google.com/p/gecko-mediaplayer/issues/detail?id=58](http://code.google.com/p/gecko-mediaplayer/issues/detail?id=58)

I stopped helping because I couldn't for the life of me compile firefox with debugging support, and then (for unrelated reasons) stopped using firefox. But the developer is very responsive, productive and helpful if you can provide enough feedback.

---

### Post by tovento on 2009-12-29
I am curious as to the settings people use in order to play videos on ninjavideo.  I finally got things seemingly working, but the program sits there building cache (as default setting is 25%).  This means it has to download quite a bit before playing.  In windows, it needs to only buffer for a few seconds before starting to stream.

How small have people set their cache levels and still had things work smoothly?  (I do realize this depends on your internet connection, but assume 5+ Mbps connection)

---

### Post by EvilGnome on 2010-01-22
A less than perfect alternative is to use only gecko-mediaplayer, and after the captcha:

- right click the player,
- copy url to clipboard,
- paste in address bar
- remove the bit before the www

and you're set to download the video from megaupload. you will be subject to all megaupload's limitations, though.

---

### Post by jake3988 on 2010-01-23
The greasemonkey script doesn't exist anymore, so I haven't tried it... but that is what I've been doing... you can do it on mplayer-plugin as well, but in order to copy the url you have to manually press play first.

I noticed that if you time it JUST RIGHT, you can force the applet to start up the url.

Here's what I do if you have mplayer-plugin:

Step 1: Enter the Capatcha
Step 2: Press play on mplayer
Step 3: Copy URL
Step 4: Wait until mplayer gives up and says 'stopped'.
Step 5: Paste the URL in a new tab and delete everything before the 'www'.  Do not press enter yet.
Step 6: Go back and press play.  
Step 7: As fast as you can, switch back again to the new tab and hit enter in the URL.
Step 6: If you timed it right, the megaupload page won't even show.  It'll wait a second or two and then immediately bring up a dialog box for download.

Ninjavideo's applet catches it and downloads it as its own without restrictions.

Occasionally it won't work, and occasionally it will yell at you for having downloaded stuff (warranted or not).  It's rare but it happens.  If it does, in about 90% of the case, waiting a couple minutes and refreshing the video and trying again will make it work.

Also, do not wait too long when loading the video.  If you wait too long, it thinks it started when it hasn't and it'll tell you it's already downloading a file when its not.  In that case, I haven't found a consistent solution other than just simply waiting 10 minutes and trying again.


Note: If there's a divx mirror, use that.  It's much slower, but it always seems to work when the video is actually there.  Usually they die pretty quick so it's only good for recent lineups.  But if it's there, try it first and save yourself the headache.

---

### Post by EvilGnome on 2010-01-24
Here's the script, I don't know why it was removed from userscripts.org.

```
// ==UserScript==
// @name           Fix NinjaVideo for Linux
// @namespace      whatever
// @description    Fixes latest broken ninjavideo helper on linux
// @include        http://127.0.0.1*/*
// ==/UserScript==
var theMoviePage = document.body.innerHTML.replace(/127.0.0.1:64653\/(www.*megaupload.*avi)/g, '/$1');

if (theMoviePage != document.body.innerHTML) {

    //just link straight to the video not through the helper
    document.body.innerHTML = document.body.innerHTML.replace(/127.0.0.1:64653\/(www.*megaupload.*avi)/g, '/$1');

    //give the first div containing the movie object an id
    document.body.innerHTML = document.body.innerHTML.replace(/<div/, "<div id='moviediv'");

    //hide the player div until we're actually allowed to connect
    document.getElementById('moviediv').style.display = 'none';

    // can't use document.write here for some reason? FireFox is throwing a security **** fit about it
    try {
        document.body.innerHTML = "<div align='center' id='downloadcounter'>Sorry, you've got to wait <div id='countdown' style='font-size: 24px; font-weight: bold; font-family: arial;'>1</div> seconds</div>" + document.body.innerHTML;
    } catch(e) {
        alert(e);
    }

    // we have to wait due to megaupload's changes
    count = 46;

    function countdown() {
        if (count > 0) {
            count--;
            if (count == 0) {
                document.getElementById('moviediv').style.display = '';
                document.getElementById('downloadcounter').style.display = 'none';
            }
            if (count > 0) {
                document.getElementById('countdown').innerHTML = count;
                window.setTimeout(countdown, 1000);

            }
        }

    }
    countdown();

}
```

---

### Post by Suicidal_SNiper on 2010-01-24
I re-uploaded the script here: [http://userscripts.org/scripts/show/67168](http://userscripts.org/scripts/show/67168) .

Of course all credit goes to shockdiode and made sure it was clear it wasn't me who created the script.

---

### Post by xpoff on 2010-02-04
Has anyone,
 ran into problem's with ninja's soon to be release update..  They are setting it up so you don't have to punch in the code which is causing conflict's with shockdales grease monkey script.

I get a blank white page when I try the updated ninja video,  I can however still download from the source.. kinda lost on this one , it's like it's starting all over..haaa no damit

The current ninja video is still running fine for me with no problem's,  thought i would throw it out there before they do the full update

Thank you for your time

Dicker

---

### Post by rknetsch on 2010-02-06
No matter what I do, Mplayer says "Loading Playlists", flashes a URL, then says "Stopped".  I get the Capcha, and everything but cant get past this point.  I have the script and Greasemonkey running and everything.  No Idea how to proceed.  I enabled DivX and unchecked the "streaming with cahing" or whatever.  Very frustrating.

---

### Post by rknetsch on 2010-02-07
Anyone?  I don't mean to pester, but this is very frustrating.

---

### Post by Laysan_A on 2010-03-01
Hi,

It's been a while, so I'm hoping you found a solution and you're happily watching away...
If that's not the case, may I recommend that you check the ninja forum and follow all their instructions. As long as you have the proper programs installed with the greasemonkey script it should work. Here's the link:
[http://forum.ninjavideo.net/index.php?topic=37751.0](http://forum.ninjavideo.net/index.php?topic=37751.0)

Personally, since mplayer doesn't have full functionality with ninja I either let it load completely and save it, or I open it with vlc from my tmp folder. Oh, you want to have caching enabled, so untick that box. Set the cache to load 100% of the video. 

Good luck!

---

### Post by shiellb on 2010-03-03
Thank you.  I followed your suggestion and everything works great:)

---

### Post by Laysan_A on 2010-03-03
Glad I could help, shiellb!

---

### Post by shiellb on 2010-03-05
Thank you for your script.  Everything works now.

---

### Post by verymagicalguy on 2010-06-23
The greasemonkey script fixed it for me as well. I tried just about everything else. Thanks!

---

