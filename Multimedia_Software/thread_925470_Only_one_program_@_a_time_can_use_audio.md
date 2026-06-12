---
title: "Only one program @ a time can use audio"
date: 2008-09-20
forum: Multimedia Software
---

### Post by renesisspeed on 2008-09-20
I think the title pretty well sums it up. 

Lets say I start up my pc and start firefox, then say... go to youtube to watch a video; Audio works with no problem. Now lets say after I watch the video I leave firefox open, and open Amarok or xmms. Neither xmms or amarok will work. 
So I close firefox, restart xmms (or whatever, IE; amarok, xmms, lmms, renoise etc. etc. etc.) & now xmms works with no problem. lets say now I stop xmms (but keep it open), & open amarok. xmms still works, but amarok will not. I could go on like this, but I think I've made my point. Does anybody have any idea how to fix this?
Also, can Alsa & Jack function simultaneously? The reason I ask is that some of the programs I use seem to do better with Jack rather than Alsa, where as others apparently use strictly Alsa.
I appreciate any input :-)

TIA - renesisspeed

PS: I read through this post "http://ubuntuforums.org/showthread.php?t=205449" and attempted to add the OSS setting to firefox & epiphany, bu it didn't seem to do much. lol

---

### Post by lovinglinux on 2008-09-20
This should fix it.

> **Tatty said:**
> Try installing

```
sudo apt-get install libflashsupport
```

This should fix flash sound problems in hardy.  Have a read of this page for more info: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by Brain-free on 2008-09-20
If the above doesn't fix it -unlikely- try changing your sound output from "pulse" to "alsa" (System -> Preferences -> Sound). That is, if you haven't already tried it.

---

### Post by renesisspeed on 2008-09-20
Thanks lovinglinux, I installed > sudo apt-get install libflashsupport but it made no difference.

I don't specifically have a problem with flash audio, its just a matter of most audio programs not wanting to get along with each other. 

For example right now I have renoise & vlc both running & each can output audio. If I now open firefox or epiphany flash audio will not work. If I then close renoise & vlc. flash audio still does not work. If I then resart firefox, flash audio will work. 

The same is true with xmms, just replace "firefox" in the above paragraph with "xmms". When I try to run xmms with any other audio program open (including firefox) I get a dialogue telling me to check that > Your soundcard is configured properly
you have the correct output plugin selected
No other program is blocking the soundcard

@ "Brain-free" 
I switched to alsa in the sound preferences dialogue. it still doesn't work. Also as you know, in that dialogue there is a button nest to each option to "Test" the setting. When no other audio programs are running, these work fine for both pulse & alsa, otherwise I get this error
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource.


Also just FYI, I have Renoise set to run through jack as it will not work through alsa if other audio apps are running, pluse it sounds better through jack.

---

### Post by eye208 on 2008-09-21
libflashsupport will make Flash (and its host application, i.e. the browser) unstable. You can easily see for yourself by browsing e.g. [http://www.imeem.com/](http://www.imeem.com/) with and without libflashsupport installed. With libflashsupport Firefox will crash quickly.

The best solution is to remove PulseAudio so that Flash (and all other apps) use ALSA directly. This will also improve latency in Jack.

---

### Post by Sycron on 2008-09-21
I have this problem too...

---

### Post by lovinglinux on 2008-09-21
> **eye208 said:**
> libflashsupport will make Flash (and its host application, i.e. the browser) unstable. You can easily see for yourself by browsing e.g. [http://www.imeem.com/](http://www.imeem.com/) with and without libflashsupport installed. With libflashsupport Firefox will crash quickly.

The best solution is to remove PulseAudio so that Flash (and all other apps) use ALSA directly. This will also improve latency in Jack.

I think you generalizing too much. The current version of Flash/Firefox will result in crashes on several sites and there are lots of threads about this. I'm running Firefox with libflashsupport for a while and I haven't a single crash for a long time, although I must admit that I'm using NoScript extension, so I only allow flash on sites that I need it. The site you provided really crashes Firefox, but I guess the problem will not be solved until the release of Firefox 3.0.2 (expected for tomorrow I guess).

---

### Post by GrandpaLeaman on 2008-09-21
If you are using Hardy, it sounds like you do not have PulseAudio properly set up. You may want to see the following thread which will walk you through the steps to do this. I did and have not had any problems playing multiple audio devices, even Flash.

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Also, it looks like there is a fix out there to get Jack to work with PulseAudio.

[http://ge.ubuntuforums.com/showthread.php?t=875378](http://ge.ubuntuforums.com/showthread.php?t=875378)

I hope this helps!

---

### Post by eye208 on 2008-09-21
> **lovinglinux said:**
> The site you provided really crashes Firefox
Only if libflashsupport is installed. You can easily test it yourself.

---

### Post by lovinglinux on 2008-09-21
> **eye208 said:**
> Only if libflashsupport is installed. You can easily test it yourself.

Yes, I understand, but doesn't mean libflashsupport makes Firefox generally unstable. The current version of Flash/Firefox alone are already unstable and the effect of libflashsupport on that site could be an isolated event. Have you tested on other flash web sites so you can be sure libflashsupport causes instability when browsing flash web sites?

---

### Post by dorukaelp on 2008-09-21
i had the same problem with the sound. from (System -> Preferences -> Sound) The devices were set 'autodetect, and i change all the devices to ALSA manually. it seems to work now.

---

### Post by GrandpaLeaman on 2008-09-21
If you read Renessispeed's post #4 he isn't saying he is having problems with Flash, and I quote:

> I don't specifically have a problem with flash audio, its just a matter of most audio programs not wanting to get along with each other.Besides libflashsupport is to fix problems with using Flash 9 with PulseAudio, if PulseAudio is properly set up.

---

### Post by eye208 on 2008-09-21
> **dorukaelp said:**
> i had the same problem with the sound. from (System -> Preferences -> Sound) The devices were set 'autodetect, and i change all the devices to ALSA manually. it seems to work now.
It works with Totem, but VLC and others still won't have sound. I tried it.

---

### Post by eye208 on 2008-09-21
> **GrandpaLeaman said:**
> Besides libflashsupport is to fix problems with using Flash 9 with PulseAudio, if PulseAudio is properly set up.
Yes. The only problem is that libflashsupport makes matters worse. Go to [http://www.imeem.com/](http://www.imeem.com/) or any other Flash-rich site and see for yourself.

Of course you can blame Flash all day long, but that doesn't change the fact that it works as soon as PulseAudio is out of the picture.

I'm not trying to evangelize anyone. If you don't like my solution, feel free to look for something else. But don't tell me I'm making this up. I am only presenting the facts. And the current situation is that the Flash/libflashsupport/PulseAudio combo is unstable while the Flash/ALSA combo is not.

---

### Post by xc3RnbFO8P on 2008-09-21
This worked for me:
[http://ubuntuforums.org/showthread.php?t=852822]("http://ubuntuforums.org/showthread.php?t=852822")

---

### Post by markbuntu on 2008-09-21
If you really want all your applications to share audio you should read my guide here. The first part is basic sound troubleshooting, the second about getting your applicatons to work together and the third is about getting them to work with jackd:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by renesisspeed on 2008-09-21
Wow!!! a lot of info here :) thank you all

@ eye208
after installing libflashsupport, i did start having problems with crashes. It has now been removed as part of one of the 'fixes' posted by grandpaleaman, however firefox/flash still crashes @ [http://www.imeem.com/](http://www.imeem.com/), otherwise it works fine.

@ GrandpaLeaman

> You may want to see the following thread which will walk you through the steps to do this. I did and have not had any problems playing multiple audio devices, even Flash.

[http://ubuntuforums.org/showpost.php...&postcount=472](http://ubuntuforums.org/showpost.php...&postcount=472)

Also, it looks like there is a fix out there to get Jack to work with PulseAudio.

[http://ge.ubuntuforums.com/showthread.php?t=875378](http://ge.ubuntuforums.com/showthread.php?t=875378)

I tried both of these (The first of which involved removing libflashsupport) I now am able to run firefox & vlc, gxine etc. at the same time. but I still can't run xmms, amarok, renoise or lmms. And only renoise will work if jack is running now. 

I think what I need to do is get alsa to accept connections from all of the programs I'm trying to use, or alternatively get everything to run through jack (possibly using a pulseaudio plugin???)
Problem is, I have no idea how to go about doing this. lol. Or should I just remove pulse?

@ ringi
>  This worked for me:
[http://ubuntuforums.org/showthread.php?t=852822](http://ubuntuforums.org/showthread.php?t=852822)
Some of the other replies to the thread don't seem too positive, esp. since the mention of increased cpu usage is made. CPU usage is of major concern to me as some of the audio opereations I will be performing are extremely cpu intensive anyway. Thank you for your input though!

---

### Post by renesisspeed on 2008-09-21
@ markbuntu:
Wow, your guide looks very comprehensive, I will have to take some time later today to go through it in full. Thank you.

---

### Post by GrandpaLeaman on 2008-09-21
> **eye208 said:**
> Yes. The only problem is that libflashsupport makes matters worse. Go to [http://www.imeem.com/](http://www.imeem.com/) or any other Flash-rich site and see for yourself.

Of course you can blame Flash all day long, but that doesn't change the fact that it works as soon as PulseAudio is out of the picture.

I'm not trying to evangelize anyone. If you don't like my solution, feel free to look for something else. But don't tell me I'm making this up. I am only presenting the facts. And the current situation is that the Flash/libflashsupport/PulseAudio combo is unstable while the Flash/ALSA combo is not.

Well I have PulseAudio set up and libflashsupport installed and have never had a problem with Firefox crashing, that is until today when I went to the web site you noted in your post and...NO MORE FIREFOX. Guess I didn't realize it was so unstable. Sorry if I ruffled any feathers. But my point is that most distros are using PulseAudio now. It might be best to get PulseAudio working for everybody by fixing any problems that may come up. Besides I believe that Flash 10rc is out and plays well with PulseAudio. I have not installed it so I'm not sure if that is true.

---

### Post by eye208 on 2008-09-21
> **renesisspeed said:**
> after installing libflashsupport, i did start having problems with crashes. It has now been removed as part of one of the 'fixes' posted by grandpaleaman, however firefox/flash still crashes @ [http://www.imeem.com/](http://www.imeem.com/), otherwise it works fine.
I've been a regular visitor to imeem.com for months. The site never crashes here. However, if I install pulseaudio and libflashsupport, the site crashes instantly every time. If I remove libflashsupport but keep pulseaudio, the site will load but I won't have sound in other apps such as VLC.

The most obvious conclusion is that whatever is being done to make Flash work with pulseaudio causes the whole thing to become unstable. I have seen it. You have seen it. It's reproducible.

Bottom line: Flash doesn't work with Pulse.

---

### Post by markbuntu on 2008-09-21
The problem is poorly written flash code, not pulseaudio. If the flash code had properly implemented OSS, ALSA , or pulseaudio protocols in its code, it would work properly in pusleaudio as every other alsa and oss and pulseaudio application does. Sometimes I wonder if those writing flash are the same people who write the buggy audacity audio interface.

Anyway, I have been using flash10b for a long time now and it works fine. I did not update to flash10b2 or and flash10rc because they seem to be worse than the 10b I have.  A little note for those following along. libflashsupport was for flash9 ONLY. It needs to be removed for flash10. Also, If yoy are using amd64 HArdy, you need to follow the guide at the top of the 64 bit forum to get flash working properly.

And the josh hoge video on imeem plays just fine and at the same time as my xmms player in pulseaudio.

---

### Post by eye208 on 2008-09-21
> **GrandpaLeaman said:**
> But my point is that most distros are using PulseAudio now. It might be best to get PulseAudio working for everybody by fixing any problems that may come up. Besides I believe that Flash 10rc is out and plays well with PulseAudio. I have not installed it so I'm not sure if that is true.
Don't get me wrong, I am looking forward to a trouble-free PA setup. But my guess is that it won't come with Ubuntu 8.10 either. And this is a major setback for Linux adoption. If you have been watching this space for a while, you certainly have noticed that the number of sound-related threads in this forum has gone through the roof.

It's a setback because all of Linux' earlier sound issues had just been resolved. ALSA had taken over, OSS was on its way out. Skype adopted ALSA, Flash adopted ALSA. Low-latency audio with ALSA, Jack and RT kernels was kicking Windows' butt even with simple HDA onboard soundcards.

Now we are in the same mess all over again. ALSA apps stop working due to Pulse, people blame it on ALSA, and some even turn to OSS4 for salvation. Again and again you see people purporting the myth that PulseAudio is necessary to enable soundcard sharing between applications. It's utterly wrong of course, but it keeps people from pulling the plug. PulseAudio's actual features are irrelevant for about 95% of users. Most of them are redundant anyway.

Eventually all these problems will be resolved. But it's a huge waste of energy that could have been spent elsewhere.

---

### Post by markbuntu on 2008-09-21
If you follow my guide you can have all your sound applications working through pulseaudio without any problems, even with jack:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The biggest problem with pulseaudio was the way it is implemented in Ubuntu, not in its inherent functionality. I do not expect this to be fixed in Intrepid either. Some minor changes have been made for Intrepid but overall many of the same inherent conflicts that were present in the faulty implementation in Hardy will be carried over.

These problems are well known and have been mostly figured out by the community but it is another matter entirely to have them implemented in the release and it is too late for Intrepid.

The biggest reason may people are moving to OSS4 is that there is no support for their cards in ALSA. This has nothing to do with PA which will be working with OSS4 fairly soon since OSS4 needs much of PulseAudios functionality which, while somewhat overlapping in ALSA, is entirely missing in OSS4.

Besides that, if OSS4 can provide a better driver interface with PA, like better device presentation so digital and other devices can be used correctly in PA, it may speed both groups to fix their drivers and move to a more standard implementation.

---

### Post by eye208 on 2008-09-21
> **markbuntu said:**
> The problem is poorly written flash code, not pulseaudio. If the flash code had properly implemented OSS, ALSA , or pulseaudio protocols in its code, it would work properly in pusleaudio as every other alsa and oss and pulseaudio application does. Sometimes I wonder if those writing flash are the same people who write the buggy audacity audio interface.
You seem to forget that Flash had just made the transition from OSS to ALSA due to public demand. Now, instead of letting Adobe get familiar with that, we introduce **yet another** sound API. Second Life on Linux already supports no less than three sound APIs (OSS, ESD, ALSA) but for some reason their code also fails to work with Pulse, just like Flash. The result: Users ask Linden Lab to implement Pulse support because, hey, it's our new **API of the day!**

I'm sorry to say this, but Linux won't make many friends this way. This is exactly why Steinberg and other big players in the pro audio business keep their hands off Linux.

> And the josh hoge video on imeem plays just fine and at the same time as my xmms player in pulseaudio.
So why can't other people with Pulse not even view the front page of that site? Which one of the 25 PulseAudio guides has the answer?

---

### Post by markbuntu on 2008-09-21
> **eye208 said:**
> You seem to forget that Flash had just made the transition from OSS to ALSA due to public demand. Now, instead of letting Adobe get familiar with that, we introduce **yet another** sound API. Second Life on Linux already supports no less than three sound APIs (OSS, ESD, ALSA) but for some reason their code also fails to work with Pulse, just like Flash. The result: Users ask Linden Lab to implement Pulse support because, hey, it's our new **API of the day!**

I'm sorry to say this, but Linux won't make many friends this way. This is exactly why Steinberg and other big players in the pro audio business keep their hands off Linux.


A good part of that is because of the childish sniping in the development community. The fact that the linux community refuses to coalesce around a single portable sound interface is frustrating to everyone but that does somehow keep things moving, sometimes forward, sometimes backwards before going forward. Right now we are on the edge of the backward to go forward part of the process.

Anyway, most companies are not really that interested yet in supporting linux so they toss the problem to a few out of favor junior associates and give them limited resources and limited time to kludge something together and we all suffer the results.

> 
So why can't other people with Pulse not even view the front page of that site? Which one of the 25 PulseAudio guides has the answer?

Not being able to even view the site has nothing to do with Pulse Audio but with adobe which has really dropped the ball on flash10 for linux so don't confuse the issue here. The original flash10b worked great, flash10b2 was terrible, flash10rc1 was even worse, flash10rc2 may be better, I am waiting to see how many people complain about it.

But anyway my guide has all the answers, or at least links to them for sound issues. Have you tried it lately? It is about 4 times the size of the OP I wrote in June. There is a link to it a few posts above.

---

### Post by eye208 on 2008-09-21
> **markbuntu said:**
> Right now we are on the edge of the backward to go forward part of the process.
We are not going forward here at all. ALSA will continue to be around. If will continue to be the basis of low-latency audio on Linux. It will continue to be the component that talks to the raw hardware. Occasionally I hear the talk, mainly originating from the OSS4 camp, that ALSA is hopelessly messed up and needs to be replaced. Yet no one is even trying to replace it. All the PulseAudio developers do is add even more cruft on top of it. ALSA's greatest asset is the fact that it works. It somehow manages to be both reliable and flexible. Together with Jack it already does 99% of the things that PulseAudio promises to do in the distant future. Where exactly is the progress in that?

> Anyway, most companies are not really that interested yet in supporting linux so they toss the problem to a few out of favor junior associates and give them limited resources and limited time to kludge something together and we all suffer the results.
And this will not change unless Linux somehow helps them to achieve things with a fraction of the resources required to maintain the Windows branch. It really looked good for a while, but since PulseAudio was introduced all of this has been thrown out the window.

You have to keep an eye on market shares here. Windows has two big audio subsystems: DirectSound and ASIO. The former is for games, the latter is for pro audio applications. How many does Linux have now? What does an OS **without** a foothold in the games and pro audio market need half a dozen audio APIs for? And how can we expect businesses to embrace all of them? The answer is: We can't.

> Not being able to even view the site has nothing to do with Pulse Audio but with adobe which has really dropped the ball on flash10 for linux so don't confuse the issue here. The original flash10b worked great, flash10b2 was terrible, flash10rc1 was even worse, flash10rc2 may be better, I am waiting to see how many people complain about it.
Wait a minute, we are not talking about Flash 10 here at all. This is about Flash 9, the plugin that libflashsupport was written for. The plugin that somehow manages to work flawlessly with ALSA despite being badly written, as you say.

> But anyway my guide has all the answers, or at least links to them for sound issues. Have you tried it lately? It is about 4 times the size of the OP I wrote in June.
I am now four times as glad not to need it as I was back in June.

---

