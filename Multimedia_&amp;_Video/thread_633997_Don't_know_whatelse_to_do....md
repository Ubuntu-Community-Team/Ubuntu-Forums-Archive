---
title: "Don't know whatelse to do..."
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by reagentz on 2007-12-07
I've been running Ubuntu 7.10 since the release Thursday in October. New to Linux but wanting out from under Windows. I have tried hard, without bugging anyone on here about this issue. I've read every blog, forum post, HowTo, comment, everything on how to get sound working with Mic under Ubuntu for gaming. Nothing has worked and I feel like it has gotten the best of me, every time I log in to play my games my friends give me a big rash of crap about me running Linux and making comments like "uh huh Linux is great huh, why can't you talk to us in teamspeak, or ventrilo, or ingame voip". I've heard it now for over a month going on 2 and I just don't think I can take it any longer.

My fantasy right now is to be able to bust up into the game and call them all punks for running Windows in voice chat, and laugh at them, and tell them Linux/Ubuntu is the @#$%! Tonight I've worked on it for 6 hours, night before 4, night before that 5, night before that 3, everyday I've worked hard at getting this to work with my sound card. I don't want to go back to Windows, it will be a sad day if I have to just to play games that I enjoy with my friends and be able to chat like old times (seems old times now). Going 2 months without doing something you've taken for granted to be able to do with your computer leisure is disheartening.

I've got ALSA the latest package installed by hand using "make", I've got Esound installed, I've got the latest OSS installed, I feel like now I've got so much stuff installed for sound I don't know what's what.

Before I could set in Prefs > Sound > Autodetect and get sound at boot and every time I load a movie in VLC or load a game. Now I have to reboot every time I want to do something, because SND BUSY comes up in errors. I PS AUX find what's tie'n it up and kill it, and do all these other jumping through hoops stuff now to even get my sound working right for one application. 

I've got an Audigy LS (I know it's not the latest greatest but still a good sound card capable of doing what I want to do). When I bring up what my system detects it shows CA0106.

What I need to do right now, is completely remove everything sound related from my system and start from scratch, and I just don't know where to begin. If anyone could help me with this I'll do whatever it takes, and it would probably be the biggest Christmas present I could get this year. My wife asked me the other day what I wanted for Christmas and I told her my sound with Mic working for my games in Ubuntu. This has consumed me, and I believe it's finally got the best of me.

Thanks in advance to anyone responding to help me.

---

### Post by eye208 on 2007-12-07
I had four sound cards so far in several computers running Ubuntu (Terratec, C-Media, Intel, Realtek) and never had a problem getting the mic to work. I remember using Skype on them for hours.

Maybe it's about time to get rid of the Audigy.

On the other hand, once the sound card has been recognized by ALSA, getting the mic to work is usually just a matter of tweaking the mixer applet. Are you sure you checked all the settings? I would start by un-muting all the faders (both input and output ones), setting them to max gain and see what happens. If you use the Gnome or KDE mixer applets, make sure all the faders and switches are visible.

I don't think installing OSS is a good idea. ESD on the other hand won't do any harm, but most of the time it is not required either.

---

### Post by reagentz on 2007-12-07
Well, it's the Gnome Mixer and no I can't afford to go buy another sound card so close to Christmas having 2 little girls to get for, so I'll have to stick with using my Audigy LS.

I did get my Mic working, I haven't be able to get my Mic working in games, I can use the sound recorder under Applications > Sound and Video. When I log into a game, or if I use Teamspeak it doesn't record my voice during a test. In Teamspeak is I select dev/dsp nothing happens, if I select the OSS option (the first one), I get a loud crashing reverb that loops back louder and louder. If I log into World of Warcraft the Mic doesn't even show up in the voice tab Mic drop-down box. I got it to work after downloading the latest ALSA and ran the "make" on it, I then opened my Multimedia Options and set both Default Output and Default Input to ALSA, Device for output the first CA0106 in the drop down which sets the pipe to H:0,0 -- for the Default Output I set it to ALSA, Device default, Pipe sets to alasasrc.

I've set the Gnome Mixer to show all the tabs, buttons, switches, everything is jacked up, and switched on including Mic Boost +20dB, only thing not selected is IE8xxxx toggle switch. In the ALSA mixer running in terminal I have the same settings.

Like I said before I feel like I've tried everything possible, now I'm getting conflicts between games and video clips and I need to reboot every time or find the process keeping the sound busy and kill it for anything to work.

---

### Post by reagentz on 2007-12-07
Oh well piss on it, I'll go back to Windows at least everything works right after install, and I can do what I want to do on my PC immediately after install.

I've came back to Linux over the years multiple times, and I always hear how helpful the Linux community is and how tight it is, but I guess that's just a myth because when you run into a real problem no one has answers, they only have answers for issues easily worked out and already has a HowTo written so they can cut and paste from it and look smart.

Thanks for all the help guys, maybe one day there will be a distro that will actually detect and allow you to configure every thing and it work right, Sure it takes 10-15 minutes to install Ubuntu, and sure it looks nice, but I'd rather take 1 hour to install something else, and everything work right than 10-15 minutes and spend 2 months to get something that should be simple enough to setup, to work.

I put off posting and asking for help for a long time, I didn't just come here as soon as it didn't work asking for someone to hold my hand. I spent hours every day reading, and trying different configuration options, this has turned into a part-time job spending 30-35 hours a week trying to figure this out on my own. I already work a full time job, and take full time courses in college, I don't need my OS to be a part-time job to configure something like a sound card to work while running multiple applications and be able to voice at the same time. If you got yours setup in one shot everything worked well for you, then congratulations; I don't need to hear how well yours works and how something like an Creative Audigy (Creative being almost a standard in sound since the mid-90's isn't good enough) good for you! I knew if I came to the community for help, as always, I would just be wasting my time posting.

Merry Christmas.

---

### Post by eye208 on 2007-12-10
> **reagentz said:**
> Oh well piss on it, I'll go back to Windows at least everything works right after install, and I can do what I want to do on my PC immediately after install.
[ Microphone not working with latest X-Fi driver?](http://forums.creative.com/creativelabs/board/message?board.id=Vista&message.id=18196)
[ Vista x64 and Microphone not working](http://forums.creative.com/creativelabs/board/message?board.id=Vista&message.id=27896)
[ Microphone intermittently choppy in Vista 64 with Audigy ZS](http://forums.creative.com/creativelabs/board/message?board.id=Vista&message.id=27853)
[ Microphone not working?](http://forums.creative.com/creativelabs/board/message?board.id=Vista&message.id=569)
[ Microphone doesn't want to work with two programs at the same time (vista64/x-fi).](http://forums.creative.com/creativelabs/board/message?board.id=Vista&message.id=26770)
[ X-Fi Microphone issues.](http://forums.creative.com/creativelabs/board/message?board.id=Vista&message.id=26490)
[ Unable to get microphone to work in Vista](http://forums.creative.com/creativelabs/board/message?board.id=Vista&message.id=14438)
[ Vista: Microphone "currently unavailable" - Soundblaster X-Fi](http://forums.creative.com/creativelabs/board/message?board.id=Vista&message.id=10294)
[ Microphone won't work with Vista](http://forums.creative.com/creativelabs/board/message?board.id=Vista&message.id=5570)
...

---

### Post by wabre on 2007-12-10
thanks eye208 for those links.

although i feel like the initial poster. it's soooo frustrating!!!

this could be the post i could have written but instead of using microphone i could just use the word "sound".

it's amazing, tried all possible things i was able to find, building up from scratch, new ALSA 1.0.15 etc etc. i installed ubuntu 5 times!!! just to find something new and try something new.

i have a main partiton with vista. in vista sometimes finding a solution to a missing driver is - compared to ubuntu - so easy! if i had to install vista 5 times just to get sound...!

it's amazing that after reading launchpads and other how-to articles, it just does not work. but most of all, in 7.04 feisty I had sound!!! 

what does compiz manager and all other great stuff mean if you can't play your music or a video? 

i have ubuntu installed now on my laptop, i won't play around anymore, nor will i uninstall it, just for the fact i am tired of it. i will wait until 8.04 is out and if that doesn't bring sound, then GNU/Linux is history for me. i am afraid i have to say it, but in those 15 years i am using windows, one install and..it just worked...

---

### Post by eye208 on 2007-12-11
> **wabre said:**
> i am afraid i have to say it, but in those 15 years i am using windows, one install and..it just worked...
Why did you switch?

It's a well-known fact that Linux requires quality hardware. No one expects Mac OS to work on a Walmart PC, but for some reason, people expect it from Linux. Why? Because Linux is free?

Nothing is free, not even Linux. The money you save by choosing Linux should be spent on quality hardware instead. For example, Linus Torvalds runs Linux on Apple hardware. He openly recommends Intel. If there was an Intel chipset in your PC, sound would work for you. It worked for me on four different machines with four different chipsets by Intel.

Linux will work with cheap hardware too -- most of the time. I had it working with a €15 C-Media soundcard. So I guess you're just out of luck.

---

### Post by mozetti on 2007-12-11
> **eye208 said:**
> Why did you switch?

It's a well-known fact that Linux requires quality hardware.

Well, that's just flat out wrong. You just pulled that statement out of the air. It's not based on anything, certainly not reality.

---

### Post by eye208 on 2007-12-11
> **mozetti said:**
> Well, that's just flat out wrong. You just pulled that statement out of the air. It's not based on anything, certainly not reality.
Actually it's based on [this interview](http://apcmag.com/7012/linus_torvalds_talks_about) with the man himself:
> **APC**: Out of curiosity, do you have anything to say to hardware manufacturers who refuse to release datasheets or specifications about the functioning of their hardware so it could operate with the Linux kernel?

**Linus Torvalds**: Is "I hope you all die a painful death" too strong?

The good news is that a lot of hw manufacturers are actually doing the right thing. Intel in particular has improved wrt open source a lot, and for that reason I tend to suggest that when buying a machine, just make sure that you buy one with Intel graphics and wireless. That takes care of the two biggest annoyances right there.

But Intel certainly isn't the only one, and we're doing fairly well in general - with just a few dark spots.

You claim the problem doesn't exist? Okay, you may take over the discussion from here.

---

### Post by mozetti on 2007-12-11
Sure, just for grins. Where in your reference does it say anything about Linux **requiring** quality hardware? Linux is well-known for resurrecting many a computer that can't run (or run well) current OS offerings from MS or Apple. On top of that, alot of cheap hardware uses the same chips as the big boys so if a name brand works, then the off-brand generally works, too.

All Linus is saying in that article is that Intel has opened up to open-source a bit, and the support for wireless and graphics (the 2 biggest annoyances with most (new) users) is better if you go with Intel chips.

Finally, I'm not going to let this further derail the subject at hand, if the original poster is still checking back (but he doesn't seem to be).

---

### Post by eye208 on 2007-12-11
> **mozetti said:**
> Where in your reference does it say anything about Linux **requiring** quality hardware? Linux is well-known for resurrecting many a computer that can't run (or run well) current OS offerings from MS or Apple.
That doesn't contradict my statement in any way. Quality hardware doesn't have to be new. It just has to be quality hardware, that's all.

> On top of that, alot of cheap hardware uses the same chips as the big boys so if a name brand works, then the off-brand generally works, too.
Again, no contradiction here. The main problem with off-brand is that you don't have control about what's inside. Most of the time the OEM won't mention it in product descriptions. If you buy a Terratec sound card you could end up with Cirrus Logic, VIA, or C-Media inside. That's quite a difference when it comes to Linux drivers, so you have to refer to 3rd party reviews in order to know beforehand what you are going to buy. Fortunately Terratec has photos of the circuit boards on their website so you can see the ICs. But many other OEMs treat their devices like black boxes. They even warn you that their product specs are subject to change without notice.

> All Linus is saying in that article is that Intel has opened up to open-source a bit, and the support for wireless and graphics (the 2 biggest annoyances with most (new) users) is better if you go with Intel chips.
The fact that he didn't mention onboard sound doesn't mean i's not part of the story.

The main reason why Mac OS has a reputation for being reliable is because it comes bundled with a set of quality hardware. Apple's Intel-based offerings are among the best you can get. And Linux will play nice with them too.

I am tired of reading posts where people blame Linux for the problems they have with hardware. If a manufacturer releases incomplete specs or none at all, there will be trouble. In order to avoid that trouble, people have to learn how to vote with their wallets -- _before_ switching to Linux!

---

### Post by mozetti on 2007-12-11
> **eye208 said:**
> The fact that he didn't mention onboard sound doesn't mean i's not part of the story.

I could just as easily say, "The fact that he didn't mention onboard sound **does** mean it's not part of the story." Who's to say which one of us is right?

> **eye208 said:**
> I am tired of reading posts where people blame Linux for the problems they have with hardware.

Sure, too bad the original poster didn't do that.

In all seriousness, I'm just having fun here. But, don't take out your general frustration with people blaming linux on this guy.

---

### Post by lancest on 2007-12-11
Linux is less tolerant of hardware faults than Windows (which overall makes it a better performer)  Windows masks hardware deficiencies often with software layers. These deficiencies are more likely to occur on cheap hardware-  such as with onboard sound cards.  Whether Linux makes hardware work might be random and unpredictable on cheap products- but hey quality is quality!

---

### Post by reagentz on 2007-12-16
Well I do believe my Asus Mobo, AMD Athlon fx 55 64 bit chip, nVidia xFx 7800 GT, 4gb of OCZ Ram, Creative Audigy, Logitech peripherals, and Panasonic Monitor, is all quality hardware, it's not some fly-by-night Acer or some brand you've never heard of straight from the bargain bin sweat shops of China.

So that shoots the statement in the foot that I need quality hardware. From which I think you're talking out your ***.

I reinstalled Ubuntu 7.10amd64 build and got my Mic working with games using only the upgrade of ALSA and not installing anything else for sound.

So anyway thanks for your input mr. need quality hardware guy, it's that attitude that will keep Linux from becoming mainstream but it's elitist attitudes like that which is 80% dominant in Linux communities to keep it from going mainstream because you want to be the only ones to say you can successfully run your computer with Linux. I think the communities in general are just as much at fault at holding back Linux sometimes as the manufactures of software and hardware themselves.

---

### Post by eye208 on 2007-12-17
> **reagentz said:**
> So that shoots the statement in the foot that I need quality hardware. From which I think you're talking out your ***.
Umm ... no. My statement is still valid. In fact you just reaffirmed it by announcing: "I reinstalled Ubuntu 7.10amd64 build and got my Mic working"

> **mozetti said:**
> Sure, too bad the original poster didn't do that.
You're right, in fact he praised Linux by saying: "Oh well piss on it, I'll go back to Windows"

You know, whenever someone comes to a Linux forum and "threatens" to switch to Windows, he counts on the Pavlovian conditioning of Linux zealots who will go out of their way to prove that Linux is superior. We've seen this numerous times. It's getting old.

By the way, complaining about elitist attitudes is hypocrisy at best, given the OP's earlier quote:

> **reagentz said:**
> My fantasy right now is to be able to bust up into the game and call them all punks for running Windows in voice chat, and laugh at them, and tell them Linux/Ubuntu is the @#$%!
If elitist attitudes were more prevalent here, people wouldn't cry for Windows at every minor obstacle. In fact elitism is the major force driving Linux forward.

---

### Post by lancest on 2007-12-17
Only costs about $5.00 to buy a cheap sound card for Linux where i live. These work great for me (if needed) when I do conversions. Anybody who is desiring to make the change to Linux should seek whatever solution makes it happen for them personally. These forums are just for gaining technical information and running with it! If there are any roadblocks- hey just go around them!  Happy Holidays!

---

### Post by wabre on 2007-12-17
i don't know why this ended up in quality hardware or whatever...the original poster complained about things that do not work, i did the same and while an older version of ubuntu worked and a new version doesn't anymore i don't really think that this has something to do with my hardware. 

if nobody is allowed to complain that there are things that do not work, how are people supposed to progress and enhance. if everything worked out of the box it would be unreal...

sure, GNU/Linux is free of charge, so nobody should "complain", but none really does, we argued that we tried so many different things and in the end we were tired because to invest lots of time in just trying to get a simple thing to work (sound) is not worth trying anymore until something better comes out...

it worked before and now not, that's it. so in windows it works, i paid for it and i am not complaining. it's just a fact and GNU/Linux does not work on my machine right now. i can get something else or stick with windows, and maybe come back to ubuntu when it works again. Not all are developers who can compile all their basic system so that it works.

cheers guys and have fun, no war please it's just a pc..

---

### Post by eye208 on 2007-12-17
> **wabre said:**
> i can get something else or stick with windows, and maybe come back to ubuntu when it works again.
Did Feisty stop working?

---

