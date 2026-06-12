---
title: "Can you get HD Trailers on apple.com to play??"
date: 2007-03-15
forum: Multimedia &amp; Video
---

### Post by herbster on 2007-03-15
I have MediaConnectivity plugin for Firefox, and if I go to a regular trailer page from apple.com/trailers, one that IS NOT HD, and then click the link and the video itself loads within Firefox, I can easily click it and play the sucker in VLC as I like, so that's great. But..

If you go to an HD trailer link, let's say here: [http://www.apple.com/trailers/paramount/shrekthethird/](http://www.apple.com/trailers/paramount/shrekthethird/)

Everytime I click that link it freezes my Firefox, I am guessing because each HD link to each size of trailer (480p,720p,1080p etc.) is actually embedded quicktime within the browser.. is there any solution to this? Can any of you view that page or other HD Trailer pages like it ok?

I have all the players, codecs, etc. installed. Everything else works fine, just this. And I reeeeally dig HD trailers :D

Help is appreciated..

---

### Post by Lord Illidan on 2007-03-15
I am using mplayer-plugin on Edgy...works fine.


Perhaps your issue is with conflicting plugins?

---

### Post by herbster on 2007-03-15
> **Lord Illidan said:**
> I am using mplayer-plugin on Edgy...works fine.


Perhaps your issue is with conflicting plugins?

Hmm, possibly? Okay, so I found this on how to install mplayer:

[http://ubuntuforums.org/showpost.php?p=1916453&postcount=1](http://ubuntuforums.org/showpost.php?p=1916453&postcount=1)

But I don't understand what to do with that? There's code there and I see commands within it but it seems like some kind of script? What exactly do I do to make that work and get the mplayer plugin, or how did you install it? Really appreciate your help.

---

### Post by Lord Illidan on 2007-03-15
I installed it with that script.

Open a text editor.

Copy the script in it.

Rename the code to mplayerplugin.sh and save it in your home directory.
Then go to a terminal.

Type : ```
sudo chmod 775 mplayerplugin.sh
```(This will make the script executable).

Now, just type :

```
sudo sh mplayerplugin.sh
``` to execute the code.

EDIT : Any more questions, please ask them here... a question unasked is a wasted opportunity :)

---

### Post by kerry_s on 2007-03-15
Works on my "VLC" using media connectivity, but i'm on wireless so i have to wait for it to download. The ipod 1 works really good, it plays without pausing all the way through.

---

### Post by herbster on 2007-03-15
Wow thanks Lord Illidan that worked perfectly!

Yeah, kerry_s that was my next question: When I load it up in VLC, how do I know when it's done loading? I mean the HD smallest one is like 30-40megs, so I'm curious.. do you just "wait it out" or is there another way...

---

### Post by kerry_s on 2007-03-15
You can set it up in preference to play until you stop it, so it will just keep starting when it reaches the end, other wise after it finishes downloading VLC will just close.

---

### Post by herbster on 2007-03-15
> **kerry_s said:**
> You can set it up in preference to play until you stop it, so it will just keep starting when it reaches the end, other wise after it finishes downloading VLC will just close.

I gotcha, I just loaded up The Simpsons movie trailer in VLC, hit play and it was black until it finished, then it repeated and played perfectly.

I'm wondering though, how would I save the dang trailer from VLC? Or what other way from those HD pages? Because the trailer re-DLs if I hit stop and play again, and it takes some time due to the size...

---

### Post by Lord Illidan on 2007-03-16
To save HD Trailers to harddisk

Follow these steps on an HD trailer page:

[LIST=1]
[*]Go to view source (CTRL+U in Firefox)
[*]Search for 720p or 1080p (or 480p if you want) and it’s the 2nd hit you want.
[*]You’ll find something close to this:
QT_WriteOBJECT_XHTML(’[http://movies.apple.com/trailers/images/hd_btn2_720p.mov’](http://movies.apple.com/trailers/images/hd_btn2_720p.mov’), ‘67&#8242;, ‘24&#8242;, ‘’, ‘bgcolor’, ‘FFFFFF’, ‘controller’, ‘false’, ‘href’, ‘**[http://images.apple.com/movies/universal/breach/breach-tlr1_720p.mov](http://images.apple.com/movies/universal/breach/breach-tlr1_720p.mov)**‘, ‘target’, ‘QuickTimePlayer’);
[*]The 1st hit (i.e. hd_btn2_720p.mov) is just the image of the button. The 2nd hit (i.e. breach-tlr1_720p.mov) is actually a file that points to where the real trailer is ‘hidden’.
[*]Take the 2nd URL and add an h between the _ and the resolution:
From: [http://images.apple.com/movies/universal/breach/breach-tlr1_720p.mov](http://images.apple.com/movies/universal/breach/breach-tlr1_720p.mov)
To: [http://images.apple.com/movies/universal/breach/breach-tlr1_](http://images.apple.com/movies/universal/breach/breach-tlr1_)**h**720p.mov
For 1080p, it would be:
[http://images.apple.com/movies/universal/breach/breach-tlr1_](http://images.apple.com/movies/universal/breach/breach-tlr1_)**h**1080p.mov
[*]Next you can enter that URL into your browser and save it when it finishes downloading or whatever. Or else use wget from the terminal to download it to harddisk like this:
```
http://images.apple.com/movies/universal/breach/breach-tlr1_**h**1080p.mov
```[/LIST]I got this from [http://www.krunk4ever.com/blog/?p=926](http://www.krunk4ever.com/blog/?p=926)

---

### Post by herbster on 2007-03-16
Thanks sooo much bro! Dang here I was thinking without the Quicktime player this wouldn't be the same, but it's better! I just used wget and it was a piece of cake and it's SO much better than using that nasty Quicktime player in WIndows.

Thx again!!

---

### Post by Lord Illidan on 2007-03-16
> **herbster said:**
> Thanks sooo much bro! Dang here I was thinking without the Quicktime player this wouldn't be the same, but it's better! I just used wget and it was a piece of cake and it's SO much better than using that nasty Quicktime player in WIndows.

Thx again!!

That's Ubuntu for ya!

---

### Post by FrancoNero on 2007-04-21
when i got to an apple page, i can play all the regular trailers, but without seeing video (i heard the audio).
with HD, it opens 480 ones fine in totem, the other ones just plain crash..... wtf...
any suggestions?

---

### Post by herbster on 2007-04-21
> **FrancoNero said:**
> when i got to an apple page, i can play all the regular trailers, but without seeing video (i heard the audio).
with HD, it opens 480 ones fine in totem, the other ones just plain crash..... wtf...
any suggestions?

What kind of video card do you have what CPU? 480 plays on most cards but you go 720 or 1080 and you need some hardware to pull that off. I just upgraded both my card + cpu and now can play all formats fine, but before, hell no... so let us know...

Also, are you using the MediaConnectivity Plugin?

---

### Post by FrancoNero on 2007-04-21
> **herbster said:**
> What kind of video card do you have what CPU? 480 plays on most cards but you go 720 or 1080 and you need some hardware to pull that off. I just upgraded both my card + cpu and now can play all formats fine, but before, hell no... so let us know...

Also, are you using the MediaConnectivity Plugin?

generic stuff that's in my laptop. it's a core2duo with a gig ram, under win xp the 1080 stuff works flawlessly.... so it's not the hardware.... i hate how complicated it is to play all the stuff under linux... that's just annoying.
uh... i think i do use that plugin

---

### Post by herbster on 2007-04-22
FrancoNero,

Okay, so If you are using it (and if not get it @ [https://addons.mozilla.org/en-US/firefox](https://addons.mozilla.org/en-US/firefox)) go to MediaPlayerConnectivity Plugin's configure, and tell me whether Quicktime is checked or not, and if so, which player is being used. It may be your VLC settings if you are using VLC. If Totem, well, I never use Totem and never have, so I won't be much help there. But if you're using VLC or even gxine, I'm sure there are some settings to consider.

However, IMO, the best way is to use the wget method Lord Illidan helped me with in this thread. I have used it numerous times for trailers since.

---

### Post by FrancoNero on 2007-04-22
well it goes for saved trailers as well, i think... but i'll look into what you suggested

---

### Post by FrancoNero on 2007-04-26
ok i installed that plugin, and quicktime is checked. as before, quicktime videos play, but i see no picture. and with HD ones, it only plays low res HD.....

---

### Post by sloggerkhan on 2007-04-26
you can use VLC to copy the trailer, too.

---

### Post by disturbedite on 2007-04-26
i believe firefox crashing (at least some times) on apple hd trailers is a known issue.  i see it about 75% of the time with ff trunk (3.0 testing) & the mplayer plugin.  i resolved it tho by using the videodownloader extension.

---

### Post by FrancoNero on 2007-04-26
I mean, it's just annoying. first it was said that feisty is gonna be really good for multimedia, but seriously, the changes from edgy are minimal. Ubuntu is still not ready for mainstream usage. Why? because it's a f****g bitch to get multimedia to run. that's bs. I am a great fan of Ubuntu and I am running it parallel now. and simple stuff just works.
but as long as linux in general (and ubuntu in particular) is not capable of delivering simple multimedia content without big-time messing around, it's not gonna be taken seriously as a desktop OS. simple as that. it might be stable (?) and reliant and secure, but well, so is windows if you disconnect it from anything elaborate and put a firewall on it. ubuntu has to learn to deal with common tasks that people use, or it will remain an operating system for people who love to mess around...... sorry for putting it that way.

next ubuntu, i wanna enter "quicktime" in the add/remove programs, i wanna click install, and then i wanna be able to use it just like in windows, or better. everything else is a joke. as long as linuxes (and this doesnt only go for ubuntu) fail at the most simple stuff, they're not gonna be taken seriously by the general public, and only if the general public is accepting linux as a viable alternative, it will be able to move on.....

---

### Post by herbster on 2007-04-26
FrancoNero, tell us how you really feel! ;)

I don't know what to tell you, it works for me and many others just fine. Do you call Sears or some store unprepared for the public because you had one idiot sales associate at one store? Although I see where you're coming from, you might wish to consider your own situation rather than blanketing Ubuntu itself for your problem.

And have you tried VideoDownloader as disturbedite suggested?

---

### Post by disturbedite on 2007-04-26
yeah, give it a try.  it works great for me and it works on *tons* of sites.

---

### Post by FrancoNero on 2007-04-26
haha sorry for the emotional outburst, haha...
but really.... oh nevermind...
i'll get it to work somehow, and when somebody asks me again, hey dude you've tried ubuntu, right, do you think it's safe to switch, i'll have to respond, no, man, unless you wanna mess around night and day to get the basic things to work, wait a few more years....
"-(

---

### Post by disturbedite on 2007-04-26
not to turn this into a fight, but i didn't have to mess with anything.  i backed up my sources.list with my repos and reinstalled with feisty this time, restored my repos and everything i ever needed was at my fingertips.

---

### Post by Lord Illidan on 2007-04-26
> **FrancoNero said:**
> I mean, it's just annoying. first it was said that feisty is gonna be really good for multimedia, but seriously, the changes from edgy are minimal. Ubuntu is still not ready for mainstream usage. Why? because it's a f****g bitch to get multimedia to run. that's bs. I am a great fan of Ubuntu and I am running it parallel now. and simple stuff just works.
but as long as linux in general (and ubuntu in particular) is not capable of delivering simple multimedia content without big-time messing around, it's not gonna be taken seriously as a desktop OS. simple as that. it might be stable (?) and reliant and secure, but well, so is windows if you disconnect it from anything elaborate and put a firewall on it. ubuntu has to learn to deal with common tasks that people use, or it will remain an operating system for people who love to mess around...... sorry for putting it that way.

next ubuntu, i wanna enter "quicktime" in the add/remove programs, i wanna click install, and then i wanna be able to use it just like in windows, or better. everything else is a joke. as long as linuxes (and this doesnt only go for ubuntu) fail at the most simple stuff, they're not gonna be taken seriously by the general public, and only if the general public is accepting linux as a viable alternative, it will be able to move on.....

Yeah, because I can see where you can do that in Windows...Is there even an add/remove feature in Windows where you can install software with one click without going on apple.com and downloading quicktime?

Way I see it it is included in the gstreamer codecs, so it can be played, so what's your problem?

---

### Post by FrancoNero on 2007-04-27
i posted my problems. i dont see any picture when i stream it, and HD versions crash my player if larger than 480p. that's my problem. installed all the codecs and stuff.

---

### Post by herbster on 2007-04-27
FrancoNero,

Are you using Beryl? And if so, ATI or nVidia? I just recalled that I had a problem with playback of various formats when I had my ATI card using Beryl. I had to go into VLC's settings and change the video output from Default to OpenGL and vice versa depending on the format. It was a pain, but that's ATI+linux for ya! ;)

And if not Beryl, try that-- change the video output from Default to OpenGL, and give it a shot.

---

### Post by FrancoNero on 2007-04-30
i dont think i use VLC, i think i use Gstreamer

---

### Post by FrancoNero on 2007-05-01
removed gxine and all that, and i set mediaconnectivity to use Mplayer now, and quicktime regularly works fine i guess, now.
still can't play any HD over 480i. i'll try the downloading trick.... (my lab rat is apple.com's hills have eyes 2 trailer page).
downloading the 720p and 1080p trailers....

result: Totem crashes, Mplayer doesn't play it, it gives me a fatal error window saying:"error opening/initializing the selected video_out (-vo) device"

---

### Post by FrancoNero on 2007-06-10
anyone? it would sure be sweet if ubuntu were able to actually play HD videos....

---

### Post by thousandrobots on 2007-08-10
FrancoNero,

I am having exactly the same problem as you. I think the issue is related to low-end graphics cards. I am using an integrated chipset, and I think the various players just can't get what they need to play anything above 480p.

I would try the download extension and if that works, use it as a workaround. 

off-topic thoughts:

I hear what you are saying about multimedia being frustrating in Ubuntu/Linux, but I think as users, we still do have to be ready to put in some elbow grease and compromise on some things. And it's important to maintain reasonable expectations. I'm just encouraging you to be willing to roll up your sleeves every now and then. I guess your point is that you shouldn't have to, but that isn't the reality of Linux right now. Ubuntu has come a LONG way in a relatively short amount of time. Given that about 5 of the 7 formats for trailers on apple.com work just fine, it might be sensible to compromise.

---

### Post by FrancoNero on 2007-08-10
I hear you. And although I think voicing one's frustration about these things is very important to bring it to the attention of the programmers, who might have other things in mind than the stuff they usually get to work with a few terminal commands, I believe that there is too much very basic stuff not working in linux/ubuntu these days that could already be working were not so much energy being diverted to high publicity stuff like ubuntu on mobiles, 3d effects and so forth, which is all nice stuff, but if basic stuff (to point out my other main point of criticism) like suspend/hibernate doesn't work, how are you expected to switch to linux, if WinDumb "JUST WORKS"....

I guess i'll wait with my HD glory for a while, hehe.

greetings from Bavaria

---

