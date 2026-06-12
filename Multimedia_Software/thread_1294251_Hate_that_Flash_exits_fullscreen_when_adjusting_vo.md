---
title: "Hate that Flash exits fullscreen when adjusting volume? DO SOMETHING about it!"
date: 2009-10-18
forum: Multimedia Software
---

### Post by martini1179 on 2009-10-18
I'm starting a campaign to get Adobe to fix their worthless Flash Player. 

Specifically, I want them to fix that [====== long string of expletives ======] bug that makes the player exit fullscreen flash when you raise/lower the volume!

Did you know that, as of the time of this writing, this bug is considered "not a bug" by Adobe? And if we don't do anything about it, it'll NEVER get fixed!

Want to kick Adobe in the donkey and get them going? 

1) Go to [https://bugs.adobe.com/flashplayer/](https://bugs.adobe.com/flashplayer/) and register. You might have to wait 5-10 minutes for the confirmation email. Click the link in the email, pretty standard. 

2) Go to [http://bugs.adobe.com/jira/browse/FP-902](http://bugs.adobe.com/jira/browse/FP-902) and tell them what you think about this whole thing. 

3) **Remember to "watch" the issue.** Just click on "Watch it" on the left-hand side.

4) **If Adobe reopens the issue, "vote" for it.** Presumably, the more votes an issue gets, the more attention Adobe will give. Voting for this issue is currently disabled, because it's "not an issue" in Adobe's version of reality.

---

### Post by martini1179 on 2009-10-28
/bump.

---

### Post by murderslastcrow on 2009-10-28
I'm doing this. This is one thing that my new Ubuntu friends always gripe about, and the fact that it's supposedly "not an issue" sounds ridiculous to me. If Adobe wants to keep ignoring the issue, I'm just gonna' pay the Gnash guys some money to come up with something better.

---

### Post by martini1179 on 2009-11-01
> **murderslastcrow said:**
> I'm doing this. This is one thing that my new Ubuntu friends always gripe about, and the fact that it's supposedly "not an issue" sounds ridiculous to me. If Adobe wants to keep ignoring the issue, I'm just gonna' pay the Gnash guys some money to come up with something better.

I hear that! With the technology world's attention increasingly turning to open source/free software (courtesy of Mozilla, Ubuntu, and, to an extent, even the Obama administration), I think it's silly that we're all still dependent on a proprietary video player. 

We have open source/free browsers, music players, video players, audio/video codecs, Office alternatives, instant messaging apps, thousands of other apps in dozens of categories, and, of course, great operating systems like Ubuntu, so why the bloody hell does the tech world still rely on Adobe Flash?! 

BTW, is anyone else surprised that Google hasn't come out with its own open-source/free streaming video software yet, and started to convert everything on Youtube to work with it?

---

### Post by lswb on 2009-11-01
My understanding may not be entirely correct, but you may notice that the details of your flash player controls are different on different sites. The website developer can customize the flashplayer they want to use for their site. So to fix the "exiting full screen" problem, every web site that uses flash would have to change the flashplayer they use. 

If you download the .flv file and play it in your own player, say totem or vlc, you can adjust the volume without exiting fullscreen.

And there is open source video on the horizon. firefox 3.5 includes html5 support which has native video capabilities. You can find some examples via google. There is some improvement necessary before it is truly useable but it is a start.

---

### Post by martini1179 on 2009-11-01
> **lswb said:**
> My understanding may not be entirely correct, but you may notice that the details of your flash player controls are different on different sites. The website developer can customize the flashplayer they want to use for their site. So to fix the "exiting full screen" problem, every web site that uses flash would have to change the flashplayer they use. 

If you download the .flv file and play it in your own player, say totem or vlc, you can adjust the volume without exiting fullscreen.

And there is open source video on the horizon. firefox 3.5 includes html5 support which has native video capabilities. You can find some examples via google. There is some improvement necessary before it is truly useable but it is a start.

Perhaps there's some truth to your implication that the server-side flash software is to blame, but it's largely irrelevant to my main point that the problem lies with Adobe, whether on the server or the client. 

I really think that with this bug being as annoying as it is, if it was an Ubuntu bug, it would have been addressed by now.

The open source video projects I've seen thus far are satisfactory, but unless a big site like Youtube begins supporting it en masse, websites will stick with Adobe. We should pressure Adobe to fix Flash player, while we wait for better alternatives to mature.

---

### Post by martini1179 on 2009-11-14
Please vote for the following bug: [http://bugs.adobe.com/jira/browse/FP-1387](http://bugs.adobe.com/jira/browse/FP-1387)

It's a duplicate of the above bug, except that this one is still open!

---

### Post by martini1179 on 2009-11-18
Ka'plah! 

Adobe has just upgraded the bug from status 'Not an Issue' to 'Internal Review.'

Voting for the bug to be fixed is open again. Head over to [http://bugs.adobe.com/jira/browse/FP-902](http://bugs.adobe.com/jira/browse/FP-902) and vote.

---

### Post by Ævar Arnfjörð Bjarmason on 2009-11-21
Given Adobe's history in the past of not fixing major issues like [non-ASCII character input]("http://www.systemed.net/blog/?p=110") on Linux this is probably something that could be fixed faster if we find a way to work around it.

As noted [in the bug report]("http://bugs.adobe.com/jira/browse/FP-902") this seems to happen because flash gets a FocusOut event from X when pressing the volume or brightness keys.

Presumably this could be worked around by hacking X not to send those events to flash if the volume or brightness adjustment keys are pressed.

It might be fruitful of someone looked into that :)

---

### Post by SR_ELPIRATA on 2009-11-23
Can't say for sure but doenst this also happen in Window$? Far as I remember it does. I'll check again to make sure....

ELP

---

### Post by jacobs444 on 2009-11-23
I have as of yet, had zero problem with flash player doing anything other than flicker when adjusting volume, or anything else fuul screen for that matter. Coud it be your graphics driver? Intel 915 here.

---

### Post by martini1179 on 2009-11-23
> **SR_ELPIRATA said:**
> Can't say for sure but doenst this also happen in Window$? Far as I remember it does. I'll check again to make sure....

ELP

No, it most certainly does not. That's why it's such a pain for a lot of us who dual boot or recently migrated from Windows.

---

### Post by martini1179 on 2009-12-02
> **jacobs444 said:**
> I have as of yet, had zero problem with flash player doing anything other than flicker when adjusting volume, or anything else fuul screen for that matter. Coud it be your graphics driver? Intel 915 here.

To whom are you referring? In Linux, the Flash Player (browser plugin) always exits fullscreen flash. If you played a local, standalone SWF file, I'm pretty sure it wouldn't exit fullscreen. 

But how many people download flash files to play locally?

---

### Post by VertexPusher on 2009-12-02
Flash exits fullscreen mode whenever something else is opening on screen: a system volume indicator, a screensaver overlay, etc.

I think this behavior is by design. It may even be triggered by Gnome in some way.

---

### Post by vredley on 2010-02-16
Bump. Please take the time to sign up here -

[http://bugs.adobe.com/jira/secure/Signup!default.jspa](http://bugs.adobe.com/jira/secure/Signup!default.jspa)

and vote for this issue here -

[http://bugs.adobe.com/jira/browse/FP-902](http://bugs.adobe.com/jira/browse/FP-902)

---

### Post by Azu on 2010-05-01
Wow. It's been over a year, somebody told them *exactly* how to fix this, yet it's *still* broken! Adobe are the most incompetent company I've ever known. What a bunch of morons. I hope they go out of business soon. Such idiocy is completely unacceptable from people in such a position.

---

### Post by benjamin222 on 2010-05-16
This isn't a flash bug. Playing .ogv files in firefox and changing the volume also exits out of fullscreen. Is there anyway just to disable the  volume pop-up notification? That would solve everything right there.

---

### Post by vkcaspervk on 2010-05-16
I use the knob on my speaker to control volume. =x 

My only issue is that the flash video/games seem to flicker/flash on all 3 of my boxes. o.O

---

### Post by vredley on 2010-05-22
> **benjamin222 said:**
> Is there anyway just to disable the  volume pop-up notification?

Install Lubuntu and map the volume keys manually.

> **benjamin222 said:**
> That would solve everything right there.

I wish.

---

### Post by hectorgrebbell on 2010-07-01
I have found that holding esc when fullscreening can 90% of the time solve the issue.
i find it can sometimes take 2-3 times before it will open fullscreen doing this, but when it will it will stay so as the volume notification appears. This does usually disable quitting with esc, so u have to use the button or double click to get out

---

