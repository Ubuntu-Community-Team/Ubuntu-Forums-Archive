---
title: "audio doesn't play in some streaming asf videos"
date: 2009-10-24
forum: Multimedia Software
---

### Post by Eathray on 2009-10-24
My streaming video works in almost every application except one: My kid's school site. They have videos he needs to watch, and my ubuntu 8.1 won't play the audio in their videos.

Gone to other streaming sites, and the vast majority of them play fine, but this one, Discovery Education won't play the audio. The files are .asf streaming movies. I looked at their requirements, and everything is fine, except their system seems to think I have java 1.5, even though I upgraded to 6. Not sure what to do about it.

Could the old java plugin still be in the browser? (firefox 3.5) Am I missing a codec? I downloaded the latest ones from firefox.

Note:
Please talk down to me. Intelligent Linux discourse may cause damage to my newly forming ubuntu brain tissue. Thanks.

Eathray

---

### Post by andrew.46 on 2009-10-24
Hi Earthray,

> **Eathray said:**
> My streaming video works in almost every application except one: My kid's school site. They have videos he needs to watch, and my ubuntu 8.1 won't play the audio in their videos.

Can you post a link to the troublesome streams?

Andrew

---

### Post by Eathray on 2009-10-24
I can try. It passes through our school site though. I don't know know if they will show an address, or if anyone could follow it without being logged into my kid's school site. I'll give it a try though.

Eathray

---

### Post by Eathray on 2009-10-24
Here is the link to one of the videos at Discovery Education. Hopefully it can be followed without being logged into the school site:

[http://gtm-media.discoveryeducation.com/videos/27658/chp929806_256k.asf](http://gtm-media.discoveryeducation.com/videos/27658/chp929806_256k.asf)

Hope it helps. Thanks for having a look, by the way.

Eathray

---

### Post by andrew.46 on 2009-10-24
Hi Earthray,

> **Eathray said:**
> [http://gtm-media.discoveryeducation.com/videos/27658/chp929806_256k.asf](http://gtm-media.discoveryeducation.com/videos/27658/chp929806_256k.asf)

Hope it helps.

Good news is that it plays fine :). The trouble you are having with this stream is that the audio is 'Windows Media Audio 9 Speech' which is a little restrictive for a school site perhaps but I guess this is how it has been done. I am not sure how you are viewing your other streaming sites but if you are using Firefox and the so-called mozilla-mplayer plugin the solution is fairly simple. You will need to add the MEdibuntu Repository:

Medibuntu - Community Ubuntu Documentation
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

This is pretty straightforward and will require you only to copy and paste a couple of lines of commands. Then you will need to run the following:

```
sudo apt-get install w32codecs
```

This will give MPlayer and its plugin the necessary codec (wmspdmod.dll) to playback the audio in your browser. (Mind you if you are running the 64bit Ubuntu you are in a bit of trouble...) If you don't have MPlayer and its plugin you will have to run:

```
sudo apt-get install mplayer mozilla-plugin
```

Hope this gets your video going :).

Andrew

---

### Post by Eathray on 2009-10-24
Do the following lines mean it's finished?

Setting up w32codecs (20071007-0medibuntu3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
eathray@ubuntu:~$

---

### Post by andrew.46 on 2009-10-24
Hi Earthray,

> **Eathray said:**
> Do the following lines mean it's finished?

Setting up w32codecs (20071007-0medibuntu3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
eathray@ubuntu:~$

Sure does. Now cross your fingers and open the site :).

Andrew

---

### Post by Eathray on 2009-10-24
I screwed up and did a force shut down (ubuntu hates that) so now I'm running check disk. Almost done, then I can test it.

---

### Post by Eathray on 2009-10-24
Okay, so... doesn't work yet. Maybe I have mplayer, but not a firefox plug-in? I don't see it in the Firefox plug-in list. Shall I search for it? Also, I noticed some Mplayer items in the Synaptic package Manager. Do you recommend one of those?

Previously I tried xine, but it didn't do anything, so I dumped it, by the way. Don't know if that matters.

Now what?

---

### Post by andrew.46 on 2009-10-24
Hi Eathray,

> **Eathray said:**
> Okay, so... doesn't work yet. Maybe I have mplayer, but not a firefox plug-in? 

Could be. Try:

```
sudo apt-get install mplayer mozilla-plugin
```

and then try the site again. With any luck...

Andrew

---

### Post by Eathray on 2009-10-25
[FONT=monospace]It says it's an invalid command for mplayer

Eathray
[/FONT]

---

### Post by Vaphell on 2009-10-25
because he messed up :-)
sudo apt-get install <package_to_install>
my box shows there is a mozilla-mplayer package, try it

or you can go to synaptic, find something with mplayer and mozilla in its name, mark it and apply changes.

---

### Post by andrew.46 on 2009-10-25
Hi Vaphell,

> **Vaphell said:**
> because he messed up :-)

Oops, my apologies indeed I did mess up. I have quietly corrected the faulty syntax I gave which of course should be:

```
sudo apt-get install mplayer mozilla-plugin
```

My apologies :(.

Andrew

---

### Post by Eathray on 2009-10-25
Okay, doesn't complain about the script this time, but says it can't find the package...

So I'll try going to the synaptic file... Pretty sure I saw two files there, maybe three... 

Eathray

---

### Post by mc4man on 2009-10-25
if it continuse to be an issue thru your brower than download and play with mplayer 
just use wget <link> , will be in home folder

Ex.

```
wget http://gtm-media.discoveryeducation.com/videos/27658/chp929806_256k.asf
```

---

### Post by Eathray on 2009-10-25
K, now I got something really screwed up. I can't post to the forums anymore. Buttons don't work (I'm on my host). I need to undue everything I've done and start over. Is there an easy solution? I tried the mplayer mozilla plug-in, that's when the buttons stopped working. Un-did it, but still doesn't work. I tried the Xine plug-in again too... nothing.

Ubuntu keeps mentioning to me that the upgrade to 9 is available... will any of this go away with an upgrade?

Eathray

---

### Post by Eathray on 2009-10-25
I guess you all have lives ;)

I'm running the updater and starting over with 9.04. Hopefully that will give me a clean slate, and we'll try this again Monday. I'll connect with you guys and re-due all the steps we tried. I may have done something out of order.

I think I should have had the mplayer plug-in before I did all the other stuff. I'll confirm with you guys first though.

Eathray

---

### Post by andrew.46 on 2009-10-26
Hi Eathray,

> **Eathray said:**
> I'm running the updater and starting over with 9.04. Hopefully that will give me a clean slate, and we'll try this again Monday.

I wonder if it is a little too late to mention that Karmic Koala will be out in 3 days and might be the best idea for a 'clean slate' approach...

Andrew

---

### Post by Eathray on 2009-10-26
Well, I don't mind running with 9.04 a while till I understand the system. Once I know how to get this thing working, all will be good.

Finished the update last night. Can we go over this again on the order of the stuff? Should I install the mplayer plug-in first, then the other steps? Do I need to remove anything I installed? (Probably will find the update removed a lot of stuff I played with).

eathray

---

### Post by vinutux on 2009-10-26
> **mc4man said:**
> if it continuse to be an issue thru your brower than download and play with mplayer 
just use wget <link> , will be in home folder

Ex.

```
wget http://gtm-media.discoveryeducation.com/videos/27658/chp929806_256k.asf
```

+1 just download that thing with this command...so U can play it with any players like vlc,mplayer etc..........

---

### Post by Eathray on 2009-10-26
Thank you for the suggestion. I appreciate everybody's help. Unfortunately it's not a practical solution for this situation.

If it was just myself downloading the occasional video, I would go with what you're saying, but this is the computer my 11 year old is using for school. He gets 3 or 4 videos to watch daily, and is only just learning computers. I'm not always here to help him find the video if it's downloaded. He needs to be able to simply click the thing and have it play.

Eathray

---

### Post by andrew.46 on 2009-10-26
Hi Eathray,

> **Eathray said:**
> Finished the update last night. Can we go over this again on the order of the stuff? 

I am also not sure what will be left after the upgrade to Jaunty. So try again with MEdibuntu, w32codecs, mplayer and the mozilla-plugin. This is the combination that successfully plays the videos in  Firefox on my system and should on yours as well.

Andrew

---

### Post by Eathray on 2009-10-26
Went through it all again, and it tells me I need the "Windows Media Audio Decoder." It tried to find it, but couldn't.

Does this mean any windows-compatible audio decoder? I should have one working right now, otherwise all the other audio wouldn't work either, right? Just isn't the latest, or the most cross-compatible? 

What next?

Eathray

---

### Post by Eathray on 2009-10-26
I'm wondering about the mplayer and the w32 codecs. Is there a way to make sure that the mplayer is using the correct codecs? Can we see what it's trying to use for asf files?

What do I do about the buttons not working? I can't post to the board on the computer we're working on since I did the medibuntu download. Something was changed in doing that (Java?).

What about mplayer settings? There's stuff in there that doesn't appear to be set up. Maybe we can talk about the important settings for streaming media.

Just trying to come up with ideas. I have the feeling something small and stupid has been overlooked.

Thanks

Eathray

---

### Post by Eathray on 2009-10-26
Okay, I put the address for the .asf videos directly into the mplayer's url option, and it opened and played with audio just fine. [B][I]That's progress, right?

[/I][/B]So, what does that mean?

1. It's not going to the right codecs automatically, but when I put the address in manually it does?
2. There's a conflict of codecs, or plug-ins?
3. There's a set-up process I'm not aware of?

I'm making progress guys, but I still need help. Come hold my hand, please.

Eathray

P.S.
I really need help with the buttons not working on the forums after I installed medibuntu. It's ridiculous to go back and forth between my kid's Linux computer and the XP host in the office. It's gotta be a javascript thing, don't you think?

Help!

---

### Post by mc4man on 2009-10-26
Just to d. check something because this doesn't seem what you'd see in regards to the mplayer plugin
> 
need the "Windows Media Audio Decoder." 

The name of the package discussed here is "mozilla-mplayer"

So what does this show if run from a terminal? (will either install or will say already installed

```
sudo apt-get install mozilla-mplayer
```

---

### Post by Eathray on 2009-10-27
Okay, it tells me I have the latest version of mplayer. Now, I believe I stumbled onto something.

Plug-in conflict. In looking at the preferences for Firefox, I found that all the asf and wav stuff was pointed either at 'Xine plug-in' which I had tried before mplayer, or 'windows media plug-in' which firefox wanted for a streaming site I went to, so I allowed it to download a while ago.

So, since I've already discovered I can play the streaming videos in mplayer if I put the url in manually, what I need now is to figure out how to make 'mplayer plug-in (in Firefox 355)' as it's described, the default player for asf and wav. It isn't in the dropdown box, and I'm not sharp enough with the Ubuntu file system to find it. Dang.

So, that's for sure what I got, just not sure how to fix it.

Eathray

---

### Post by andrew.46 on 2009-10-27
Hi Eathray,

> **Eathray said:**
> Plug-in conflict. In looking at the preferences for Firefox, I found that all the asf and wav stuff was pointed either at 'Xine plug-in' which I had tried before mplayer, or 'windows media plug-in' which firefox wanted for a streaming site I went to, so I allowed it to download a while ago.

I ope this is not becoming too frustrating :). I attach a screenshot showing how the MPlayer plugin is set on my system to play asf/asx files.

Andrew

---

### Post by Eathray on 2009-10-27
Frustration level: 3 of 5 :(

Not too terrible. I have Puppy Linux on my laptop and, same thing, setting up the sound was a minor nightmare.

I think Linux is worthwhile however. I don't want to erase viruses anymore. My kid's been playing Doom online with the computer we're working on and he hasn't gotten a single pop-up in the two weeks we've been playing with Ubuntu (unlike the other partition with Win2k).

Okay, so what do I need to do? Reload some of the plug-ins? How do I straighten this out? Is there a tool that allows me to point to this plug-in and say, play that file?

---

### Post by Eathray on 2009-10-27
Okay, I went into the Synaptic Package Manager, set all my Java packages for re-install, and boom, Java Script is now working again. ***Hurray for me!!! ***

I can now post from the computer we're working on again. Something in Medibuntu alters the Java settings, so that people know.

Continuing to work on .asf issues. Some of the streaming .asf files Discovery Education uses work, while others do not (which I am able to view by manually entering the url of the video into mplayer), but we did find a couple that played.

For those that don't, Firefox is now calling the problem a naming error ("there was a problem with the name of the file") but continues to request permission to search for the now infamous plug-in, 'Windows Media Audio Decoder.'

Progress, but ain't there yet. I'm going to keep posting everything I do, and maybe some of this stuff will trigger an idea from you guys.

Thanks, and keep your input coming please. If it helps me, I'm sure it will help others too.

Eathray

---

### Post by Eathray on 2009-10-27
sooo....

If I can play an .asf by manually putting in the url, why won't it play automatically when the link is clicked?

Open to all thoughts...

Eathray

P.S.
I've had minor Java script issues... could the problem be the link, not the video? If so, how would I test it?

---

### Post by Eathray on 2009-10-28
Help please...

Any thoughts whatsoever.

Eathray

---

### Post by Eathray on 2009-10-28
If I don't have all the Java components I need, could that effect playing movies, i.e. the info in the link isn't read correctly?

Here's a snap shot of the package manager I have. There's a lot of Java stuff I could get, but I don't know what most of this stuff is, and the descriptions are pretty innocuous. Which of these do you guys have, and what should I have?

Eathray[IMG]file:///home/eathray/Desktop/Screenshot-Synaptic%2520Package%2520Manager%2520.png[/IMG]

---

### Post by andrew.46 on 2009-10-28
Hi Eathray,

It is great that you can play the file manually with MPlayer, so some progress has been made :). But playback of the file does *not* require any form of Java, is this a requirement of the website page that provides the link? If you could provide the address of the page it would probably be helpful.

All the best,

Andrew

---

### Post by Eathray on 2009-10-28
I can give the address of the page, but it's a secure site. I just noticed that a few of the buttons don't work here and there, so I've been wondering if the java or javascript isn't right on the page could that prevent the browser from using the right plug-in to open the page that's on the other side of the link. Anyway, here's the address of the page:

[http://schools.connectionsacademy.com/content/chrome/online/default.aspx?idSection=95052&idLesson=77998&idWebuser=130793](http://schools.connectionsacademy.com/content/chrome/online/default.aspx?idSection=95052&idLesson=77998&idWebuser=130793)

Now, what did you think of the picture I posted? There's quite a few Java packages I could download. Do you think I need any of that stuff? How does it compare to what you have downloaded in your package manager?

Any thoughts please...

Thanks

Eathray

---

### Post by Vaphell on 2009-10-30
unless that page in question is java based, these packages won't do any good.
Javascript is a programming language used by webbrowsers to do all that fancy stuff impossible to achieve in plain html/css - it just works in any modern browser, java on the other hand is a fullblown programming language running programs in its virtual machine (though it can be plugged into the browser just like flash is). They share similar name but that's pretty much it.

---

### Post by Eathray on 2009-10-30
Then I can assume I don't need any of those additional Java items shown in the picture? Java 6 has everything I need?

K, you mentioned html. I had something unusual happen. Went to play a vid on YouTube today. It said I needed an html plug-in for a wmv file, (which is also Microsoft? Like asf?). If my theory about the link not giving the browser the information it needs to open vid files is correct, could that be an html problem? Is there a package I can download, a default html editor? There was also a problem opening an aspx audio file the other day. same problem?

(Your English is very good by the way. What are you doing in Poland? Work?)

Thanks,

Eathray

---

### Post by andrew.46 on 2009-10-31
Hi Eathray,

I wonder if you could post a similar screenshot to mine below that demonstrates which program is called to handle asf/asx files? I have changed from the mplayer plugin to gecko-mediaplayer but you can see the idea from the image. As you may know you simply type *about:plugins* into the browser address bar.

All the best,

Andrew

---

### Post by Eathray on 2009-10-31
K, Here's the screenshot. I haven't figured out how to use the pointer yet... sorry.

Eathray

---

### Post by andrew.46 on 2009-10-31
Hi Eathray,

> **Eathray said:**
> K, Here's the screenshot. 

In that case I am a little stumped :(. If you have the MPlayer-plugin configured correctly, and your screenshot seems to demonstrate this, you have a copy of MPlayer and the w32codecs installed you should be able to play this file in Firefox. My only thought is that perhaps you also have totem-mozilla installed which can cause a little trouble. What is the error message when you click on the link?

Andrew

---

### Post by Eathray on 2009-10-31
I do have totem, although I don't know why. should I get rid of it?

If I uninstall totem, should I also uninstall/reinstall mplayer plugin?

Eathray

---

### Post by andrew.46 on 2009-10-31
Hi Eathray,

> **Eathray said:**
> I do have totem, although I don't know why. should I get rid of it?

Not *Totem* itself, but the plugin that Totem uses for Firefox called *totem-mozilla*. But don't uninstall anything yet!! Is there an error message when you click on a link to open the video? This error message will tell if totem-mozilla is being called instead of the MPlayer plugin.

All the best,

Andrew

---

### Post by mc4man on 2009-10-31
Something does seem a little odd here.

If you had totem-mozilla installed it would certainly overide the mplayer-mozilla plugin but I'd think you'd see that in about plugins (totem)

I'm wondering if in firefox -> edit -> preferences -> applications if you've set it to totem instead of having on 'windows media player plugin' (see screen

so if totem-mozilla is not installed maybe check there.


(( if all else fails you could set for an auto download and play in mplayer itself, - your son wouldn't have to do anything other than d.click on a link and wait a bit longer for playback to start.
That would be set in same firefox -> preferences -> applications, you'd just pick "use other" and browse to /usr/bin/mplayer


But the mplayer plugin, whether mplayer-mozilla or the gecko-mediaplayer one should work no problem

---

### Post by Eathray on 2009-10-31
Clearly you guys are brighter than me. As soon as we finish doing the Halloween thing, I'll get on it and get back to you guys in the morning or maybe tonight.

Eathray

---

### Post by Eathray on 2009-11-01
The Firefox preferences do say the Windows plug-in is handling asf/asx. Got a screen shot for you.

Eathray

---

### Post by Eathray on 2009-11-01
The Firefox preferences do say the Windows plug-in is handling asf/asx. Got a screen shot for you.

Eathray

---

### Post by Eathray on 2009-11-01
This screenshot shows plug-ins Totem at the bottom and Mplayer right above it. Is this the conflict your thinking of?

Eathray

---

### Post by mc4man on 2009-11-01
open up synaptic package manager, search totem, and if the totem-mozilla package is installed (green box), then mark for removal and click apply.

Then try your link again

---

### Post by Eathray on 2009-11-01
Alright, guys... removing the Totem-Mozilla plug-in made the link at Discovery Education work, although it downloaded the file first instead of just streaming it. Not sure why that is, but it's nearly livable.

as I mentioned previously, I ran across an audio file that also wouldn't work:

It's a flash file labeled aspx. I know it's a kind of flash because my flash blocker makes me click the button on my other computer before it will play. which one of those plug-ins should be running aspx?

Making Real Progress, thanks to you guys.

Eathray

---

### Post by Eathray on 2009-11-01
Streaming is no longer working. The Mplayer plug-in shows now and does try to download if the thing is a clip (like the school site), but if it's a streaming channel, like watching tv online, Mplayer tries, but then stops. It won't receive it as a stream, only a download. Is there a setting to play with?

Eathray

---

### Post by andrew.46 on 2009-11-02
Hi Eathray,

> **Eathray said:**
> This screenshot shows plug-ins Totem at the bottom and Mplayer right above it. Is this the conflict your thinking of?

Sure is :). Took me more time than I care to admit to work out why the gecko-mediaplayer was not intercepting the streams I was trying to watch!

All the best,

Andrew

---

### Post by Rumpty on 2009-11-02
On Karmic here. I'm having the same trouble playing an audio file in the browser. It plays fine if it is opened directly in Gnome Mplayer, but will not play with the FF plug-in.

[http://static.radionz.net.nz/assets/audio_item/0019/2115271/ckpt-20091102-1707-NZ_troops_come_under_fire_in_Afghanistan-m048.asx](http://static.radionz.net.nz/assets/audio_item/0019/2115271/ckpt-20091102-1707-NZ_troops_come_under_fire_in_Afghanistan-m048.asx)

---

### Post by Eathray on 2009-11-02
Andrew,

It works, but not completely. The mplayer is now playing those streaming files from the link, but as downloaded clips, not streams, and streams are now gone elsewhere in windows formats (replies #49 &#50).

Should I reinstall the mplayer plugin? will that give it some kind of updating?

Eathray

---

### Post by Rumpty on 2009-11-02
Eathray, if you haven't already, install "GStreamer plugins for mms, wavpack..." That may help to get the streaming going.

Streaming of .asx files with Gnome Mplayer, using the browser plugin work fine for me in Ubuntu 9.04. It even works in the Google Chrome browser on 9.04, so it is nothing to do with Firefox specifically, I guess.

I haven't got it going in 9.10 yet though.

---

### Post by Eathray on 2009-11-02
cool. I shall give it a go.

Eathray

---

### Post by Eathray on 2009-11-03
I looked in the synaptic package manager and found a lot of gstreamer stuff, but about half of it's already installed. I didn't see a specific package for mms and wavpack. Can you give me the names of the files, or maybe post a screenshot of your gstreamer section so I could compare it to my own?

Thanks

Eathray

---

### Post by mc4man on 2009-11-03
> ....looked in the synaptic package manager and found a lot of gstreamer stuff

Wouldn't know exactly, tend not to use, (probably the bad plugin), but the more useful plugins would be

gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll
bad (1st listed
bad-multiverse (4th listed
ugly (1st listed
ugly-multiverse (4th listed  

You may again wish to post a link to troublesome stream(s)

---

### Post by Rumpty on 2009-11-03
> **Eathray said:**
> I looked in the synaptic package manager and found a lot of gstreamer stuff, but about half of it's already installed. I didn't see a specific package for mms and wavpack. Can you give me the names of the files, or maybe post a screenshot of your gstreamer section so I could compare it to my own?

Thanks

Eathray

The one you want is  

gstreamer0.10-plugins-bad

I installed it from the Ubuntu Software Centre, (not that that makes any difference) Click on Sound and Video, and you will see the description there in the Gstreamer we want, which mentions mms, wavpack...

---

### Post by Eathray on 2009-11-04
I'm going to check that out. None of the packages in Synaptic Package Manager describe the mms or wavepack stuff.

In the meantime, because there was a conflict with plug-ins, I'm posting all the plugins from my Firefox About:Plugins page, so that maybe somebody can spot another conflict. So, what's wrong with these pictures? See the next post too since this one limits me to 5 uploads.

Eathray

---

### Post by Eathray on 2009-11-04
Here's the rest of the pics:

Eathray

---

### Post by Rumpty on 2009-11-04
Take it from me, Eathray, the gstreamer I think is well worth trying is the one I mentioned, gstreamer0.10-plugins-bad. That is how it appears in Synaptic.

Another thing to try is installing the Opera browser. I did that, and it streamed the .asx files straight off, no fuss at all, whereas Firefox and Chrome still refuse to do that in Karmic.

You have Gecko Mediaplayer installed? All the above hinges on that.

---

### Post by Eathray on 2009-11-04
The synaptic package manager says I have the file: gstreamer0.10-plugins-bad, along with quite a few other gstreamer files. I'll post a pick of what I got so you can see.

I'm kind of stuck with Firefox for my kid's school site because they only accept Firefox and Explorer (and I just can't bear to install a wrapper and go back to Explorer). Also, it's supposed to be Firefox for Windows, but Firefox has a User Agent Switcher, so that's my go-around.

I do not have Gecko Mediaplayer installed. If I install it, will it conflict with Mplayer? Do I remove one before trying the other?

Eathray

p.s.
Please look at my other pics from about:plugins. When Andrew.46 had me get rid of the totem plugin, I was suddenly able to view the asf files, even though it was a download instead of a stream. There could be another conflict there. Thx.

---

### Post by Rumpty on 2009-11-04
Right, you have the  gstreamer0.10-plugins-bad, so we will forget about that.

I have both gecko mediaplayer and mplayer installed, and there doesn't seem to be any conflict. Basically I am following the advice in the Comprehensive Multimedia & Video Howto, a sticky at the start of this multimedia forum. Have a look at Part 2/5, Audio and Video Streaming.

Installing Opera was just a suggestion to see if it behaved differently from Firefox. You don't have to keep using it, it might just serve to clarify (or confuse!) the situation. It was good to see that, for me, it just worked streaming my .asx file, whereas FF and Chrome don't work.

As for your plugin list, don't think I can help much there, as there is so much listed, it's confusing. For instance, I don't have vlc installed, but the vlc plugin is there?

---

### Post by Eathray on 2009-11-04
I hear you on the confusion. I don't know where half that stuff came from. Some of it must have been there from the beginning, but some of it came when I went somewhere and Firefox requested a plugin to play something, like the quicktime plugin. I have wondered if that one is a problem since it seems to be attached to more than just apple files.

I think the vlc came with Ubuntu, 'cause I don't remember Firefox asking for it.

I'll try Opera tomorrow, just to see if it makes a difference. Thing is, streaming used to work when I had Totem, but it was conflicting with Mplayer on my kid's school site. Now my kid's school site works as a download, but any streaming microsoft format doesn't. (Flash still works though. My kid lives for YouTube). I'll try Gecko tomorrow and see what happens. Then maybe I'll dump vlc and see what that does, since you don't have it and you can stream.

Thx.

Eathray

---

### Post by Rumpty on 2009-11-05
Made some progress here. It looks like there was a plugin conflict, as you suspected. Went to /usr/lib/mozilla/plugins and compared what there in Ubuntu 9.04 (where streaming works) and 9.10 (where streaming doesn't work)

There were about a dozen in 9.10, all told, so I removed the extras, mostly to do with totem, and put them in a spare folder. Now streaming an asx file works in FF and Chrome! The plugin list in FF is now much depleted.

Screenshot of my plugins attached.

---

### Post by Eathray on 2009-11-05
Are you using Mplayer at all, or did you dump it for the Gecko stuff?
 
Eathray

---

### Post by Rumpty on 2009-11-05
Mplayer is still installed, along with Gnome Mplayer.

---

### Post by Eathray on 2009-11-05
I tried some directions from one of the stickies at the beginning of this topic, reloaded Mplayer manually, no luck.

Discovered that even though I used to have vlc stuff in Firefox through Totem, I didn't have Vlc or its plugin itself, so I disabled everything and installed vlc and it's plugin to see if it could do anything. Nothing.

There are a crapload of settings in Mplayer that I haven't done a lot with. Could someone post some snapshots of their Mplayer settings so I can so what other people have done differently then me and eliminate the the obvious? Thanks.

There's something I'm missing here, but I don't know what it is. Gotta be something simple and stupid.

Eathray

---

### Post by Rumpty on 2009-11-05
Agreed, you shouldn't be having all this trouble. Maybe someone else will chip in with some advice. 

In the meantime, can you stream this audio?
[http://static.radionz.net.nz/assets/audio_item/0005/2119487/ckpt-20091105-1716-Hide_apologises_to_PM-m048.asx](http://static.radionz.net.nz/assets/audio_item/0005/2119487/ckpt-20091105-1716-Hide_apologises_to_PM-m048.asx)

---

### Post by Rumpty on 2009-11-06
Eathray, I think you should probably ignore that link in my previous post, and the fact of whether or not the link audio streams.

Maybe we have lost the thread of your original problem?

---

### Post by Eathray on 2009-11-06
But it's still centered around windows stuff... asf, wmv, etc. I played with an internet tv site last night, and only one of about ten wmp channels would stream.

Snapshots please. What are your settings for mplayer out there?

Thx

eathray

---

### Post by Eathray on 2009-11-06
Here are some shots of my current Mplayer preferences, under the tab, Codex and Demuxer. There are no packages selected. Should there be, or does Mplayer use what it wants to use?

Help please.

Eathray

---

### Post by Eathray on 2009-11-06
Here's a list of my current plug-ins. Is this stuff right?

Thanks.

Eathray

---

### Post by Eathray on 2009-11-07
[CENTER]***[SIZE=5]Help[/SIZE]***
[/CENTER]

---

### Post by Rumpty on 2009-11-08
This is no good Eathray, link still not working!
Here is my plugin list. Firefox, Ubuntu 9.04. It is a bit different, but your Discovery link works, picture and sound.

Also, I think the preferences you have screenshots for are from the wrong player, should be from Gnome Mplayer? In any case, my Gnome Mplayer prefs are default, I think. Make minimum cache size equal 32.

---

### Post by Eathray on 2009-11-08
Okay, Here it is:

1.)  I turned on the cache in Mplayer,
2.)  Uninstalled the Mozilla-Mplayer plug-in,
3.)  Installed the Gecko plug-in for Gnome Player and Mplayer,

And it works (mostly).
The .asf files at my kid's school site now stream, and most of the .wmp files at other streaming sites now work as well. There's a few that don't, but there were always a few that didn't with Windows too, ('cause the site is doing something funky with embedding or layering I suppose).

That's ***good enough!*** I can fiddle with the other stuff as I go.

Special thanks to Rumpty, andrew.46, and Vaphell for your assistance.

Eathray

---

### Post by andrew.46 on 2009-11-08
Hi Eathray,

> **Eathray said:**
> That's ***good enough!*** I can fiddle with the other stuff as I go.

Good to see it all worked out, I know it was a bit of a struggle :).

Andrew

---

### Post by Eathray on 2009-11-08
Nasty affair.

Now how do I change this thing to let people know it's fixed?

Eathray

---

### Post by Eathray on 2009-11-08
I figured it out... it is now marked as "solved."

Eathray

---

### Post by Eathray on 2009-11-09
Rumpty,

Instead of Gnome player, try the Mplayer, which is Gnome based, with the Gecko plug-in for Gnome and Mplayer. That's what I have. I'm assuming you have the Midibuntu package and the windows codecs... doesn't appear to me you have to reload them, but I did run the Janitor when I made so many changes I couldn't keep track of them anymore.

Eathray

---

