---
title: "Nuendo user. XP user, new to Linux"
date: 2008-02-26
forum: Multimedia Production
---

### Post by FieldbornTemple on 2008-02-26
Hello. I'm currently an XP pro user. My computer is something of an AMD +4000, 3gig DDR ram, 160gig ATA HDD, crappy 16meg PCI video card, Presonus Firepod via firewire. 
I'm very accustomed to using Steinburg's Nuendo 3 for all of my recording needs. I use Waves VST pluggin bundle. 
I have my XP setup to run as lightly as possible so as to give as much available speed to Nuendo. Still, sometimes I have problems when working with a dozen tracks. 
I was always impressed with APPLE MAC computers and their OS abilities but haven't yet dumped that much money into a hobby. So I'm looking at Linux. Ubuntu came up as very popular but I'm having some trouble finding answers to my questions. 
Is it possible to run Nuendo in Ubuntu? Do I have to use something like WINE or another way? What about ASIO and VST pluggins? Will they work too? I hear Steinburg hasn't released some code to allow VST to work in linux, but it seems like some people have made it work?
I've heard about Ardour but am reluctant to believe the claims that it is as good as Nuendo and ProTools. I admit I don't know because I haven't tried yet. But still I'll be honest in saying I'm hightly skeptical. 
If Nuendo won't work and I need to use Ardour, will Waves VST pluggins work with that?
One last question... I'm not a programmer. I'm very capable working in and fixing problems in XP. But other than some HTML I don't know anything about code... Can a newbie handle Ubuntu and setting up recording things like ASIO, VST, firewire?
Thanks!

---

### Post by eye208 on 2008-02-27
Forget it.

Linux has the potential to become the #1 audio platform in the future. The foundation (realtime capability, low latency audio path) has already been laid. But the applications are not there yet. Ardour will become interesting when its MIDI functionality is ready, but so far it is only for audio, i.e. no replacement for Cubase/Nuendo/Logic. Steinberg refuses to consider the idea of porting anything to Linux at this time. This is in part because of their user base that, despite all the flaws of Windows Vista, will bash you for even mentioning the Linux topic in their forum. From all the communities I've seen so far, musicians are the most conservative and backwards one. They love to write lyrics about changing the world etc. but that's all BS. They are (in general) more afraid of change than anyone else.

I'm afraid you're stuck with Windows for the time being. This is going to change some day, but that day has not yet come.

---

### Post by FieldbornTemple on 2008-02-27
Vista? Curses to Vista. Waste of time.
Sorry, had to get that out. Anyway, thank you for your response. I was afraid of that. So, Nuendo is a no go. About Ardour. I can work around the lack of MIDI functionality. Is Ardour capable of ASIO and VST? And other than MIDI, is Ardour very capable? More so than a generic dime-a-dozen multi-tracker?

---

### Post by robeast on 2008-02-27
eye makes some good points but I disagree when he says you can't replace your current setup. I was running about the same thing: XP, Nuendo 3, FruityLoops, and I used ProTools extensively in the studios at my school. Linux audio apps go way further than replacing all of those programs. Ardour lacks MIDI, but is a multi-track audio masterpiece. There are many other MIDI sequencing programs out there and, thanks to JACK, the low latency audio server you'll be running, you can route your MIDI events and audio signals around wherever you want!

Now I've gone and gotten myself all worked up. 

If you want to assess whether Linux could be right for you, check out this article I wrote. It should give you an idea of what the most essential programs available have to offer. 

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

No programming required, but you'll probably have to unlearn some windows habits like defragmenting your hard drive, paying for software and needing antivirus garbage. Don't worry about that processes list, run as many as you want. 

Here's my usual studio setup: My computer was a mid-range system when I put it together three years ago. I run a multi-track recording program, a midi sequencing program (also with audio capabilities) and a softsynth all synced up through JACK, there's a DVD ripping, I'm bitting some Simpsons episodes and I've got firefox open to an online manual. This is all spread out over eight desktop spaces mapped on an eight-sided 3D shape that I can spin around all willy-nilly. AND the windows wobble. Always with the wobbling.

Now I've gone and gotten myself all worked up again.

The cherry on top? I use a Presonus Firepod as well which required no configuration at all after installing the Ubuntu Studio audio packages. Didn't even have to install a silly system tray application! 

I'm seriously dude.

---

### Post by robeast on 2008-02-27
Forgot to mention this, no VST support due to steinberg licensing, but I've heard of something called dssi-vst that is supposed to enable their use? There are many (too many) Linux Audio Developers Simple Plugin Architecture (LAPSDA) plugins which are comparable to the plugins that come with commercial software (and much more abundant). I'd recommend buying some outboard gear with the money you save on software.

---

### Post by kayosiii on 2008-02-27
Ardour quite a competant DAW... It does not do Asio (There is no need, windows has Asio, Linux has Jack). Currently licensing issues prevent the distribution of copies of Ardour with VST support you can get this if you build your own copy... The method used to support VST is not always reliable so your milage may vary depending on how portable the plugins you need really are. Linux has its own native plugin api's ladspa and now lv2. There are quite a few plugins written in these formats - though possibly not what your looking for. Also with the power of Jack it is possible to plug the outputs of any jack capable app into the inputs of any other jack capable app and vice versa. This allows you to chain complete applications together instead of using plugins it really is quite powerful once you get used to it.

---

### Post by FieldbornTemple on 2008-02-28
> **robeast said:**
> eye makes some good points but I disagree when he says you can't replace your current setup. I was running about the same thing: XP, Nuendo 3, FruityLoops, and I used ProTools extensively in the studios at my school. Linux audio apps go way further than replacing all of those programs. Ardour lacks MIDI, but is a multi-track audio masterpiece. There are many other MIDI sequencing programs out there and, thanks to JACK, the low latency audio server you'll be running, you can route your MIDI events and audio signals around wherever you want!

Now I've gone and gotten myself all worked up. 

If you want to assess whether Linux could be right for you, check out this article I wrote. It should give you an idea of what the most essential programs available have to offer. 

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

No programming required, but you'll probably have to unlearn some windows habits like defragmenting your hard drive, paying for software and needing antivirus garbage. Don't worry about that processes list, run as many as you want. 

Here's my usual studio setup: My computer was a mid-range system when I put it together three years ago. I run a multi-track recording program, a midi sequencing program (also with audio capabilities) and a softsynth all synced up through JACK, there's a DVD ripping, I'm bitting some Simpsons episodes and I've got firefox open to an online manual. This is all spread out over eight desktop spaces mapped on an eight-sided 3D shape that I can spin around all willy-nilly. AND the windows wobble. Always with the wobbling.

Now I've gone and gotten myself all worked up again.

The cherry on top? I use a Presonus Firepod as well which required no configuration at all after installing the Ubuntu Studio audio packages. Didn't even have to install a silly system tray application! 

I'm seriously dude.

That is very comforting to hear! I'm so glad my firepod will work. I was worried about it. Dissapointing that the VST plugins aren't supported but I'll have to try the dssi-vst and find out. My Waves plugins go along with me everywhere I go.
One question about the firepod though, or maybe the question should be about Ardour? 
Can you change the sample rate past 44000 and bit rate to 24 as you can with the firepod control panel in Windows, and Nuendo?

---

### Post by Stochastic on 2008-02-28
Yup the firepod goes to it's full 96000 24bit state.

Also the VST plugins can work (even in ardour, though that takes a bit of work) if you install the right components, but not all as some have dependencies in their code.  Right now it's trial and error with VST plugins.  These were the steps I had to take to get VST running on my Feisty install (I decided not to bother with my Gutsy install because everything I needed was in the LADSPA set) [http://ubuntuforums.org/showthread.php?t=557466](http://ubuntuforums.org/showthread.php?t=557466)

---

### Post by FieldbornTemple on 2008-02-29
Fantastic!
So to sum up... 
Firepod works very well. Ardour is worth trying to work with. VST is possible but I have to make that happen (I'll be visiting these forums a lot for that part!) And Nuendo is not Linux compatible.
I'll give the 64bit studio ubuntu program a try and see how far I can get before I need to return for help. This'll be my first time in Linux. Can't wait! Unfortunately I'm at work away from my recording computer for a few weeks but now I have a plan of aproach for when I get back.
Thank you all for all of your input!

---

### Post by robeast on 2008-02-29
If your computer is used primarily for recording then 64bit is the way to go. However, if you want to do something like view flash content on websites, you should use 32bit. Last I checked, the Linux flash player was only working in 32bits which is pretty crucial for the web experience...unfortunately. I found random inconveniences like that in a few other places, too. I'd switch back to 64bit in a heartbeat of those were fixed.

---

### Post by FieldbornTemple on 2008-03-01
> **robeast said:**
> If your computer is used primarily for recording then 64bit is the way to go. However, if you want to do something like view flash content on websites, you should use 32bit. Last I checked, the Linux flash player was only working in 32bits which is pretty crucial for the web experience...unfortunately. I found random inconveniences like that in a few other places, too. I'd switch back to 64bit in a heartbeat of those were fixed.

I think I'd like a bootable version setup as 64bit for recording so I can use all of the power of my processor. And if possible I'll setup a second bootable version as 32bit so I can do all my everyday computing needs, email, internet, chat, word, simply photoshop...

---

### Post by jobsonandrew on 2008-03-23
> **robeast said:**
> If your computer is used primarily for recording then 64bit is the way to go. However, if you want to do something like view flash content on websites, you should use 32bit. Last I checked, the Linux flash player was only working in 32bits which is pretty crucial for the web experience...unfortunately. I found random inconveniences like that in a few other places, too. I'd switch back to 64bit in a heartbeat of those were fixed.
Hey I was just reading this (because I'm interested to find out more about Ubuntu's audio capabilities) and thought I'd point out that you can get flash working on a 64 bit Ubuntu system.. you can search these forums for a script that sorts it all out for you automatically... it essentially uses the 32 bit flash plugin, but wraps it with nspluginwrapper so that the 64 bit environment can understand it :)

---

### Post by TimH1980 on 2008-03-23
Can anyone tell me who succesfully has a FOSS studio decorated how you can automate midi parameters? I read that it's not possible in Rosegarden so there must be another way?

What I want to do is e.g. run a filter of a synthesizer over a midi chanel via my midi controller and record automation over it (automate the filter sweep). This in one of the most important things why I'm still on the pc/mac site for making music. 

If somebody can help me out with that I would be really happy :-) And has somebody worked with Ableton Live in the past for it's mixing and warping facilities? Did it work out to find some good foss alternatives? Maybe a combination of several programs through jack? 

Let me know! Thanks in advance!

---

