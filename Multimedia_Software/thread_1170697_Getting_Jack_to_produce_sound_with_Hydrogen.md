---
title: "Getting Jack to produce sound with Hydrogen"
date: 2009-05-26
forum: Multimedia Software
---

### Post by emu42 on 2009-05-26
I've been having problems for many months, but now I'm determined to get Jack to work. I've been using Timidity for a synth in Rosegarden, but now  I need other things (such as Ardour and Hydrogen) which need Jack to synchronize.

So first, I want to get Hydrogen to work with Jack. When I go to preferences, the only option that produces a sound is ALSA. I am using a Sound Blaster Audigy card. And like I said, Timidity works fine as a synth. And Jack isn't producing any error messages. But Hydrogen (or any other program for that matter), when using Jack drivers, doesn't produce a sound under any settings.

Jack settings:

[http://img148.imageshack.us/img148/1980/jacksettings.png](http://img148.imageshack.us/img148/1980/jacksettings.png)

Hydrogen settings:

[http://img43.imageshack.us/img43/6276/hydrogensettings.png](http://img43.imageshack.us/img43/6276/hydrogensettings.png)

---

### Post by emu42 on 2009-05-26
Another interesting thing, when I uncheck Enable Track Outputs everything works fine, but with no audio. When I check it then Hydrogen gives me error messages. Not sure what that's all about.

---

### Post by ibuclaw on 2009-05-26
Some nice small prerequesites I'd like to suggest:
What kernel do you use?

Ubuntu offers a kernel with patches/tweaks for realtime responses.
```
sudo apt-get install linux-image-2.6.28-3-rt
```

Alternately, you can [download the 2.6.29 kernel]("http://www.kernel.org/"), [apply the patches to enable realtime processing]("http://www.kernel.org/pub/linux/kernel/projects/rt/") and build using make-kpkg.

The primer being the most simplest way, of course :)

Next, edit the limits.conf file:
```
gksu gedit /etc/security/limits.conf
```
and put in
```
@audio - memlock 512000
@audio - rtprio 99
@audio - nice -10

```
Near the bottom before "# End of file"

Save and quit, then run:
```
sudo usermod -a -G audio $USER
```
To ensure that you are part of the audio group, then reboot into the new realtime kernel.

In the JACK Setup window, you can check the "Realtime" parameter now.

To the point of your question though:
Start the JACK Server, then run Hydrogen.
After Hydrogen starts, switch to the JACK window and click the **Connect** button, and you should be able to connect up the input/output between the soundcard and application/s

Regards
Iain

---

### Post by emu42 on 2009-05-26
Wow, thanks for you input, Jack works now! And so do the other Jack programs, all except for Rosegarden. Everything works as normal on Rosegarden (including the Jack transport), but there is simply no sound. I *think* this has to do with Timidity, since it still pops up in the connections. I'm not sure how to end Timidity. Plus, if I do, I don't know how to then get Rosegarden to use Jack as its synth. I tried going through the connections in Jack, and even if I disconnected Timidity and Rosegarden, they stayed connected.

Anyways, here's a couple screenshots of the Rosegarden Midi settings if it's helpful:

[http://img26.imageshack.us/img26/8194/rosegardengeneralsettin.png](http://img26.imageshack.us/img26/8194/rosegardengeneralsettin.png)

[http://img245.imageshack.us/img245/5001/rosegardenmidi.png](http://img245.imageshack.us/img245/5001/rosegardenmidi.png)

Again, thank you so much for your effort.

---

### Post by dawiba on 2009-05-27
Sorry to hijack the thread a bit, but I'm unclear on a couple of things

Tinivole - you say

'Next, edit the limits.conf file:
Code:

gksu gedit /etc/security/limits.conf

and put in
Code:

@audio - memlock 512000
@audio - rtprio 99
@audio - nice -10

Near the bottom before "# End of file"'

In mine, those three lines come after '# End of file'. Everything still seems to work fine though. Does it matter? If I do

grep audio /etc/security/limits.conf

I get

@audio - rtprio 99
@audio - nice -19
@audio - memlock unlimited

I assume this is okay?

The other thing is, you say to download a kernel and then apply patches. Should they all be applied or just some? If it's just some, how do I know which ones?

Sorry for the daft questions, but I don't know the answers.

Thanks.

---

### Post by ibuclaw on 2009-05-27
> **dawiba said:**
> Sorry to hijack the thread a bit, but I'm unclear on a couple of things

Tinivole - you say

'Next, edit the limits.conf file:
Code:

gksu gedit /etc/security/limits.conf

and put in
Code:

@audio - memlock 512000
@audio - rtprio 99
@audio - nice -10

Near the bottom before "# End of file"'

In mine, those three lines come after '# End of file'. Everything still seems to work fine though. Does it matter? If I do

grep audio /etc/security/limits.conf

I get

@audio - rtprio 99
@audio - nice -19
@audio - memlock unlimited

I assume this is okay?

Yep, that is fine. I suppose you are already running UbuntuStudio then. ;)

> 
The other thing is, you say to download a kernel and then apply patches. Should they all be applied or just some? If it's just some, how do I know which ones?

Sorry for the daft questions, but I don't know the answers.

Thanks.

That was just an optional alternative, if for some unknown reason the 2.6.26-3-rt kernel was not available in the repository.
I choose to build my own, as I build systems rather than install them. ;)


Regards
Iain

---

### Post by dawiba on 2009-05-27
> **tinivole said:**
> Yep, that is fine. I suppose you are already running UbuntuStudio then. ;)

That was just an optional alternative, if for some unknown reason the 2.6.26-3-rt kernel was not available in the repository.
I choose to build my own, as I build systems rather than install them. ;)


I'm actually running the regular Ubuntu with just the applications I want installed from the repositories. I'm running 2.6.26-3-rt kernel for music anyway, so I guess that's fine.

Thanks for the reply

---

### Post by ibuclaw on 2009-05-27
> **emu42 said:**
> Wow, thanks for you input, Jack works now! And so do the other Jack programs, all except for Rosegarden. Everything works as normal on Rosegarden (including the Jack transport), but there is simply no sound. I *think* this has to do with Timidity, since it still pops up in the connections. I'm not sure how to end Timidity. Plus, if I do, I don't know how to then get Rosegarden to use Jack as its synth. I tried going through the connections in Jack, and even if I disconnected Timidity and Rosegarden, they stayed connected.

Anyways, here's a couple screenshots of the Rosegarden Midi settings if it's helpful:

[http://img26.imageshack.us/img26/8194/rosegardengeneralsettin.png](http://img26.imageshack.us/img26/8194/rosegardengeneralsettin.png)

[http://img245.imageshack.us/img245/5001/rosegardenmidi.png](http://img245.imageshack.us/img245/5001/rosegardenmidi.png)

Again, thank you so much for your effort.

hmm... do synths work?

If you can find one, I'd probably suggest that you use a GM soundfont/synth instead.

Regards
Iain

---

### Post by emu42 on 2009-05-27
Well when Rosegarden is running by itself with Timidity, it works fine, but when I open up Jack and use other stuff, it doesn't have any audio.

---

### Post by markbuntu on 2009-05-27
Timidity is probably not connecting to jack. You should set rosegarden to use jack and close it and then start it again after you start jack or tell rosegarden to start jack. Personally I like to start jack first and then the apps and then connect them up with patchage.

If you use patchage you can see all your applications and midi devices etc all in one place and can change connections by clicking on them. It really makes things so much easier.

---

### Post by emu42 on 2009-05-27
> You should set rosegarden to use jack

I was wondering about that. I don't know how to tell Rosegarden what to use. I don't see it in the settings, just the Jack transport option.

Also I tried to load SoundFonts instead of just using MIDI, and failed miserably. But I suppose Jack will be able to handle SoundFonts as well as MIDI if/when I get Rosegarden to work, correct?

---

### Post by emu42 on 2009-05-27
When I'm in Patchage/Jack connections, what specifically should be connected, and should anything be disconnected? I've been wondering, since I tend to just connect everything to everything so I can't go wrong. That's fine, right?

---

### Post by markbuntu on 2009-05-28
If it works for you, it is fine but you should play with the connections and see what happens so you can figure out what is optimal for your particular needs.

I have not messed around much with soundfonts so I can't help you there but you should try the Multimedia Production Forum. It can be a little slow at times but the people who hang out there really know their stuff.

---

### Post by emu42 on 2009-05-28
Okay, I'm going to ask around about soundfonts in the Multimedia Production forum.

Thanks for all your responses.

---

