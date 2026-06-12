---
title: "Quicktime and Second Life"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by Angelbeast on 2008-02-02
Okay i was told taht i need Quicktime in order for tv to work in Second Life. Howdo i do this? Do i need to use wine?

---

### Post by DJ_Peng on 2008-02-02
As long as you have the Gstreamer pugins for totem installed you shouldn't have any problem using the video content in SeconfLife.

---

### Post by Angelbeast on 2008-02-02
> **DJ_Peng said:**
> As long as you have the Gstreamer pugins for totem installed you shouldn't have any problem using the video content in SeconfLife.

I looked in package manager and it looks like i do have Gstreamer installed but still no vieo.

---

### Post by DJ_Peng on 2008-02-02
Do you have all the plugins added? I'm not sure which one you specifically need, but I'd take all the good, bad, etc., plugins. And some content still won't work, but I think that's because they used the newest and "best" version of QT to encode it. There are a couple sims that wont show the video content for me but there's nothing that can be done about those. You can also ask the Linux Client Users group in SL. They've helped me a lot in the past.

---

### Post by Angelbeast on 2008-02-03
> **DJ_Peng said:**
> Do you have all the plugins added? I'm not sure which one you specifically need, but I'd take all the good, bad, etc., plugins. And some content still won't work, but I think that's because they used the newest and "best" version of QT to encode it. There are a couple sims that wont show the video content for me but there's nothing that can be done about those. You can also ask the Linux Client Users group in SL. They've helped me a lot in the past.

I did a search in Synapti and installed anything that said it played quicktime files and that justseemed to slow down the SL client.

---

### Post by DJ_Peng on 2008-02-03
You may have been better off doing a search for gstreamer. But I'm not sure what to tell you about the slowdown. Have you asked in the Linux Client Users group in SL? That may be your best bet. You;ll have to join the group first (it's free), but they're a wealth of info on how to do things with the SL Linux clients.

---

### Post by Angelbeast on 2008-02-03
> **DJ_Peng said:**
> You may have been better off doing a search for gstreamer. But I'm not sure what to tell you about the slowdown. Have you asked in the Linux Client Users group in SL? That may be your best bet. You;ll have to join the group first (it's free), but they're a wealth of info on how to do things with the SL Linux clients.

I uninstalled what i had installed and that took away the slowdown. Then iinstalled only the gstreamer quicktime pugin and still noluck. I even tried quicktime itself in wine with no luck. But others are ale to see it. I don't get it. 

Idid try the usergroup but no one seemed very interested in helping *LOL*

---

### Post by DJ_Peng on 2008-02-03
Yeah, the group in SL can feel like a crapshoot. Try asking again during more daytime hours in the US. I find getting help can really depend on who and how many people are on. I've asked a question around this time and gotten nothing, but then asking again even 12 hours later found people more than willing (and able) to help. Just remember Sunday's the Super Bowl so the helpful folks may be off engaging in Super Bowl activities.

I will give you this list of plugins I have installed. I'm not sure which one did the trick for me, but I was enjoying the video content at Journey Rock Band in SL just last night.

> gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

---

### Post by Angelbeast on 2008-02-03
> **DJ_Peng said:**
> Yeah, the group in SL can feel like a crapshoot. Try asking again during more daytime hours in the US. I find getting help can really depend on who and how many people are on. I've asked a question around this time and gotten nothing, but then asking again even 12 hours later found people more than willing (and able) to help. Just remember Sunday's the Super Bowl so the helpful folks may be off engaging in Super Bowl activities.

I will give you this list of plugins I have installed. I'm not sure which one did the trick for me, but I was enjoying the video content at Journey Rock Band in SL just last night.

Okay i'll give that a try...And you're not having any slowdown with those?

---

### Post by eye208 on 2008-02-03
Here's a trick for you: If you start Second Life from a terminal window, each time you enter a parcel with a media stream you will see its URL printed in the terminal (along with lots of other log info). You can use the URL to view the stream outside SL or even save it to disk.

But don't tell anyone. It's a secret! :mrgreen:

---

### Post by DJ_Peng on 2008-02-03
> **Angelbeast said:**
> Okay i'll give that a try...And you're not having any slowdown with those?
I'm running on an old comp with less than a gig of RAM and a very old video card  so I wouldn't know if it's slowing down. :D Plus I tend to run test versions of SL so I don't have a good benchmark of how fast it's supposed to run on my machine without all the gstreamer plugins.

---

### Post by Angelbeast on 2008-02-03
> **DJ_Peng said:**
> Yeah, the group in SL can feel like a crapshoot. Try asking again during more daytime hours in the US. I find getting help can really depend on who and how many people are on. I've asked a question around this time and gotten nothing, but then asking again even 12 hours later found people more than willing (and able) to help. Just remember Sunday's the Super Bowl so the helpful folks may be off engaging in Super Bowl activities.

I will give you this list of plugins I have installed. I'm not sure which one did the trick for me, but I was enjoying the video content at Journey Rock Band in SL just last night.

Okay well i tried all of them...still nothing althogh ow SL doen't freeze when i tyr to play the tv so that's alwys good *LOL*

---

### Post by Angelbeast on 2008-02-03
And i also notice now that the  top button lights up just for a second like it starts to play but then goe dark again like it looses the stream or something...

---

### Post by Angelbeast on 2008-02-03
*bump*

---

### Post by Angelbeast on 2008-02-03
Okay i had an idea. I have Totem xine installed so i can play dv's. Do i need to have Totem Gstreamer instead?

---

### Post by DJ_Peng on 2008-02-03
Gstreamer has the codecs that will decode QT in SecondLife. I'd definitely trade the gstreamer xine for gstreamer totem. There are players for DVDs that use gsteramer. I view DVDs in Ogle, TOtem and VLC, just for some suggestions.

---

### Post by Angelbeast on 2008-02-03
> **DJ_Peng said:**
> Gstreamer has the codecs that will decode QT in SecondLife. I'd definitely trade the gstreamer xine for gstreamer totem. There are players for DVDs that use gsteramer. I view DVDs in Ogle, TOtem and VLC, just for some suggestions.

Yeah i just switched..i'm about to give it a try

---

### Post by Angelbeast on 2008-02-03
Still no luck...This starting to really frustrate me *LOL*...

The stop buttin on the video stream light up just for a second like it's about to start then goes right back out...

---

### Post by Angelbeast on 2008-02-04
> **DJ_Peng said:**
> Gstreamer has the codecs that will decode QT in SecondLife. I'd definitely trade the gstreamer xine for gstreamer totem. There are players for DVDs that use gsteramer. I view DVDs in Ogle, TOtem and VLC, just for some suggestions.

Hey could i possily trouble you to come look at my tv and see if it works for you?

---

### Post by DJ_Peng on 2008-02-04
Are you using the same sim for checking the video? There are some that won't even work for me. Try checking the video at Journey Rock Band. I know the video there works for Linux users. My sis was there just the other day when I went to see her.

---

### Post by Angelbeast on 2008-02-04
> **DJ_Peng said:**
> Are you using the same sim for checking the video? There are some that won't even work for me. Try checking the video at Journey Rock Band. I know the video there works for Linux users. My sis was there just the other day when I went to see her.

kay i'll try that. Thanks.

---

### Post by Angelbeast on 2008-02-04
> **DJ_Peng said:**
> Are you using the same sim for checking the video? There are some that won't even work for me. Try checking the video at Journey Rock Band. I know the video there works for Linux users. My sis was there just the other day when I went to see her.

I can't find it in the search *LOL*

---

### Post by Angelbeast on 2008-02-04
bump

---

### Post by Angelbeast on 2008-02-05
oky well still no luck...there's nothing else i can try?

---

### Post by Angelbeast on 2008-02-05
silly question...does second life and firefox use the same plugin for quicktime streams?

---

### Post by Angelbeast on 2008-02-05
*bump*

---

### Post by DJ_Peng on 2008-02-05
I'm not sure if SL and Fx use the same plugin, although I know Fx's plugin is pretty specific. It may use similar stuff under the hood.As far as the Journey sim goes, I don't have the SLURL handy, but my sister did put it in [her blog post about their new island]("http://nancib.wordpress.com/2008/01/27/journey-set-to-rock-secondlife/").

You may not want to bump the thread so often. Sometimes it's just taking us a little extra time to get in to post. I did see a notice in my email earlier today but RL had me busy enough that I couldn't post until now.

---

### Post by eye208 on 2008-02-05
> **Angelbeast said:**
> silly question...does second life and firefox use the same plugin for quicktime streams?
Yes, both SL and the Quicktime plugin for Forefox use GStreamer by default, i.e. if Firefox and Totem can play a particular stream, SL should be able to play it too.

If you open a stream in Totem, you will be prompted to install additional codec plugins if necessary. This prompt will not appear in SL though! That's why you should pick any non-functional stream URL from the viewer's log output and open it with Totem at least once. After successful installation of the required codec(s) the stream should work in SL too. It definitely worked for me this way.

---

### Post by Angelbeast on 2008-02-05
> **DJ_Peng said:**
> I'm not sure if SL and Fx use the same plugin, although I know Fx's plugin is pretty specific. It may use similar stuff under the hood.As far as the Journey sim goes, I don't have the SLURL handy, but my sister did put it in [her blog post about their new island]("http://nancib.wordpress.com/2008/01/27/journey-set-to-rock-secondlife/").

You may not want to bump the thread so often. Sometimes it's just taking us a little extra time to get in to post. I did see a notice in my email earlier today but RL had me busy enough that I couldn't post until now.

Well firefox is using mplayer...could my problem be that mplayer is trying to be the default player for sl too? mplayer is doning the same thing in the browser with quicktime streas tht is happenng in SL...it acts like it's going to play for a second then does...

---

### Post by Angelbeast on 2008-02-05
If i uninstall mplayer will that make gstreamer the default for quicktime streams?

---

### Post by DJ_Peng on 2008-02-05
As it says on the page for the [gstreamer-tools]("http://packages.ubuntu.com/gutsy/utils/gstreamer-tools") package, Gsteramer isn't a player, it's "a streaming media framework, based on graphs of filters which operate on media data." Totem is the player (with [totem-gstreamer]("http://packages.ubuntu.com/gutsy/gnome/totem-gstreamer")) that many if us use successfully to enjoy the streaming media content in SecondLife. I'll let others post what specific media players they use, but just deleting Mplayer won't let you play any media unless you replace it with something.

---

### Post by Angelbeast on 2008-02-06
> **DJ_Peng said:**
> As it says on the page for the [gstreamer-tools]("http://packages.ubuntu.com/gutsy/utils/gstreamer-tools") package, Gsteramer isn't a player, it's "a streaming media framework, based on graphs of filters which operate on media data." Totem is the player (with [totem-gstreamer]("http://packages.ubuntu.com/gutsy/gnome/totem-gstreamer")) that many if us use successfully to enjoy the streaming media content in SecondLife. I'll let others post what specific media players they use, but just deleting Mplayer won't let you play any media unless you replace it with something.

well this just doesn't look very promising then *LOL*

---

### Post by DJ_Peng on 2008-02-06
You could always go with Totem, and use the totem-gstreamer package (with the plugin set) to view the SL content. It's a matter of choosing which player you want to use for everything else and deciding if its' worth letting Totem hand the QuickTime content. The totem-gstreamer files simply direct totem to use the gstreamer plugins. If you want to use something else it should still work the same, I was just saying what works for me computer.

---

### Post by Angelbeast on 2008-02-06
> **DJ_Peng said:**
> You could always go with Totem, and use the totem-gstreamer package (with the plugin set) to view the SL content. It's a matter of choosing which player you want to use for everything else and deciding if its' worth letting Totem hand the QuickTime content. The totem-gstreamer files simply direct totem to use the gstreamer plugins. If you want to use something else it should still work the same, I was just saying what works for me computer.

Yes if totem will work then that' what i wnt. How do i change it? *LOL*

---

### Post by DJ_Peng on 2008-02-06
> sudo apt-get install totem totem-gstreamer
You may already have one or both of them installed, but if you do it will simply let you know.

---

### Post by eye208 on 2008-02-06
SL will always use GStreamer, no matter if totem-gstreamer is installed or not.

---

### Post by Angelbeast on 2008-02-06
> **DJ_Peng said:**
> You may already have one or both of them installed, but if you do it will simply let you know.

yeah it's telling me i already have everything..it's still not working...so i'm just out of luck it seems?

---

### Post by DJ_Peng on 2008-02-07
I've got nothing. Hopefully someone else will have some suggestions.

---

### Post by jdunn on 2008-02-15
I'm running Kubuntu on Gutsy.  I downloaded the plugins DL_Peng suggested from the repositories.  I also went to Journey Rock Band in SL.  I get sound but no video when I try to play video streams in the game.  I can't check the official SL Linux Client forums because I will not give them credit card info (required to access their forums :razz:).  I have no trouble playing quicktime video&sound through Firefox using the mplayer plugin.

---

### Post by eye208 on 2008-02-15
> **jdunn said:**
> I have no trouble playing quicktime video&sound through Firefox using the mplayer plugin.
As pointed out earlier in this thread, SL uses the GStreamer framework for video playback. So whatever plays fine in Totem will also play fine in SL. You can find out the URL of any parcel media stream by looking at the console output of the SL viewer. Try to open that URL in Totem. You will eventually be prompted to install additional GStreamer plugins. After completing the installation, the video should play in Totem. Then it should play in SL as well.

Make sure you have the universe and multiverse repositories enabled, otherwise some plugins may be out of reach for the package manager.

---

### Post by DJ_Peng on 2008-02-15
Thanks for the note about the other repos, eye. I enable them automatically when I do a reinstall and forget that others may not have them enabled.

---

### Post by jdunn on 2008-02-15
Thanks, eye208.  It took me a few minutes to figure out exactly what you meant by "console output of the SL viewer".  After realizing there is no console window within the game, I used 'tail -f ~/.secondlife/secondlife.log' and ran the game in windowed mode just to test things out.  One of these two packages 'gstreamer0.10-ffmpeg' or 'gstreamer0.10-pitfdll' had the Journey Rock Band videos playing for me in Totem and in SL (had to restart SL so plugins would work for it).  Now, I just have to figure out what plugins will work for some of my favorite SL places.

---

### Post by jdunn on 2008-02-16
Okay...Does anyone know why many movies at different places will not play?  I've heard that some movies are "bad" or corrupted.  However,  I know the admin of one place who says her movies run perfectly for her (she uses Windows XP) from americafree.tv.  Thinking that maybe my hw firewall was blocking the streaming video, I opened ports suggested at [http://secondlife.com/whatis/faq.php]("http://secondlife.com/whatis/faq.php").  This didn't solve the problem.  While trying to play streams from americafree.tv, I found the URL somewhere in my SL log file but I wasn't seeing it in the log file (tail -f) as I pressed "Play".  Also, I can play the americafree.tv video streams directly with totem.

---

### Post by Angelbeast on 2008-02-16
I just tried playing the strem i'm hving issues with directly in totem and it didn't work. Here's the error i got in the screenshot...I have gstreamer installe...what else do i need?

---

### Post by DJ_Peng on 2008-02-16
In addition to totem-gstreamer, you also need to have gstreamer0.10-pitfdll from the Universe repos installed. You may need another group of plugins installed, but I have them all and can't remember which one did the trick for me. I'm pretty sure it was the pitfdll.

---

### Post by Angelbeast on 2008-02-16
> **DJ_Peng said:**
> In addition to totem-gstreamer, you also need to have gstreamer0.10-pitfdll from the Universe repos installed. You may need another group of plugins installed, but I have them all and can't remember which one did the trick for me. I'm pretty sure it was the pitfdll.

okay going to try it now

---

### Post by Angelbeast on 2008-02-16
it says i have it already...i hve several other plugins as welll

---

### Post by eye208 on 2008-02-18
> **jdunn said:**
> It took me a few minutes to figure out exactly what you meant by "console output of the SL viewer".  After realizing there is no console window within the game
"Console output" usually refers to the output of an application that you see if you run that application from a terminal window.

When you're at a location where a video won't play, please open the map, click the "Copy SLURL to clipboard" button on the lower right, then paste that URL here.

---

### Post by msand_nj on 2008-02-18
I had this problem too, and solved it by editing SecondLife_i686_1_18_5_3/secondlife and uncommenting the following line: 

export LL_BAD_OSS

That might work for  you.  If not, try the others one at a time?

Mark

---

### Post by jdunn on 2008-02-29
> **eye208 said:**
> When you're at a location where a video won't play, please open the map, click the "Copy SLURL to clipboard" button on the lower right, then paste that URL here.

eye208,   I'm running version 1_19_0_5 of SL now and I still can't watch videos here

[http://slurl.com/secondlife/Cyprus/208/179/22](http://slurl.com/secondlife/Cyprus/208/179/22)
 
...and I can only watch some of the videos here

[http://slurl.com/secondlife/Misfits%20Hideaway/176/110/349](http://slurl.com/secondlife/Misfits%20Hideaway/176/110/349)

---

### Post by jdunn on 2008-03-06
bump.  See Message #50.

---

### Post by jasonwatkins on 2008-04-07
anyone ever have any joy over this ?

i've been trying for weeks to get video playing in Second Life with no luck.

---

### Post by kostkon on 2008-04-07
> **DJ_Peng said:**
> In addition to totem-gstreamer, you also need to have gstreamer0.10-pitfdll from the Universe repos installed. You may need another group of plugins installed, but I have them all and can't remember which one did the trick for me. I'm pretty sure it was the pitfdll.

> **Angelbeast said:**
> it says i have it already...i hve several other plugins as welll

The *gstreamer0.10-pitfdll* package is useful only when you combine it with the *w32codecs* package that provides many codecs that are taken from Windows (some for QT are included).

Thus, add the [*Medibuntu*]("http://medibuntu.org/") repository to your software sources list, [as explained here]("http://help.ubuntu.com/community/Medibuntu"), and then install the *w32codecs* package. 

There are chances that after doing the above, the QT videos will now play just fine.

---

