---
title: "no sound except in front speakers (Gutsy)"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by xjgnsdof on 2007-10-21
Im dual booting Ubuntu Gutsy Gibbon and Windows XP. I have Logitech X-540 5.1 surround speakers and a Sound Blaster Audigy SE which work perfectly in Windows XP. Last night, I ran GParted to shrink my Windows partition and allocate that space to Ubuntu. As far as I can tell, both operations were successful, as both partitions reflect the changes.

When I restarted my computer this morning, I got no sound in Ubuntu. I saw in another forum post to enter ¨sudo apt-get update && sudo aptitude dist-upgrade¨ and now I get sound in only the front two speakers.

In Volume Control Preferences, the selected device is ¨CA0106 (Alsa mixer)¨. When I open Volume Control, I notice that the sound in the front two speakers changes when I adjust Änalog Front," but nothing happens when I adjust ¨Analog Rear¨ or ¨Analog Side¨ or ¨Analog Center.¨ I have no idea what went wrong between GParted and my restarting Ubuntu this morning; my surround sound had been working impeccably before it.

---

### Post by xjgnsdof on 2007-10-21
I did a fresh install of Ubuntu, after which the system was just as it was the first time I installed it when the speakers all worked. However, the front two speakers are still the only satellites getting sound. Again, all of the speakers work in Windows XP when I boot into that on the same machine. Please help me out, as I'm trying to set up VMWare to play my Windows games in Ubuntu, which isn't feasible until I can get the sound kinks worked out first.

---

### Post by shad0w_walker on 2007-10-21
Have you checked the volume manager? It might be that your audio channels are muted, I had that same problem with my 5.1, might also be that the volume sliders for those channels are hidden. 

P.S. What sort of games are you planning on playing in VMware? The graphics support from what i understand is still pretty experimental/basic so anything overly advanced might be an issue. Also bare in mind that you will incur a pretty big performance hit due to running the whole OS as well.

---

### Post by xjgnsdof on 2007-10-21
In Volume Control under CA0106 (Alsa mixer), the bars are turned all the way up.

As for VMware, I have a pretty sick video card if you'll see my sig, so the performance lag isn't likely to be an issue.

---

### Post by shad0w_walker on 2007-10-21
I don't think it matters how kick*** your system is. Its a matter of how much of your graphics power the VMware drivers can utilise (Likely not a great amount) I would be suprised if you got any modern, intensive game to run decently. Anyway, that's a matter of what i understand, if you have success with it, awesome on you and I'm sure that will make some people very happy.

Back to the main issue. Where are you trying to play this audio from? It's possible that the program is defaulting to stereo sound (A safe bet on most systems)

---

### Post by xjgnsdof on 2007-10-21
This happens whether I'm on Youtube or watching a movie on VLC. Even Ubuntu's login sound only plays on the front left and front right speakers. No clue how it happened.

And you're right about gaming in a virtual machine or emulator in Ubuntu. I read that they pretty much only run old games, which I don't plan on playing. I think I'm just better of biting the bullet and dual booting. It saves me the headache, and I can at least proudly say that I can do everything else through Ubuntu.

---

### Post by shad0w_walker on 2007-10-21
Make sure you have a known source of 5.1 because i don't ever recall youtube doing 5.1 sound and any random video on VLC is very likely to be 2.1 at best. Get a DVD or something, anything with **known** 5.1 sound and use that as the test material.

If it still only comes out of the front speakers then check the program preferences to make sure it is outputting in 5.1.

---

### Post by xjgnsdof on 2007-10-21
I put in a DVD movie and still only heard sound from the front two speakers. I watched the movie in VLC. Once again, only when I moved the slider bars for "Analog Front" in my volume manager could I change the volume.

---

### Post by shad0w_walker on 2007-10-21
Did you check that the 5.1 audio was playing on the DVD? I believe most programs (Including VLC assume you have stereo. Check in the Audio menu and see if there are any other audio tracks to play, one of those should be 5.1

---

### Post by xjgnsdof on 2007-10-21
Nope. It just says "Disabled" or "Track 1," and the latter yields sound in the front two speakers, while the former results in silence.

---

### Post by xjgnsdof on 2007-10-21
I popped in one of my other DVDs, and under "Audio Device" was an option for 5.1 sound. After selecting that option, I got sound from all the speakers, albeit not all the time--only in certain scenes. How do I make sound come out of every speaker the way it comes out of the front speakers? I'm kind of peeved about my Windows login wav sounding richer than my Ubuntu login wav. In Windows, my YouTube videos air from all of the speakers; in Ubuntu, they only come from the front two. I can only control the speakers through the "Analog - Front" option in the volume manager. Doesn't anyone know how to fix that?

---

### Post by xjgnsdof on 2007-10-21
up

---

### Post by xjgnsdof on 2007-10-22
I just realized that I don't have a .asoundrc file when I look at the hidden files in my Home folder. Is that a problem?

Also, when I plug in my headset mic, I can only control the volume in the headset by moving the "Analog Front" sliders in the volume manager. There is something seriously wrong with my surround sound, here.

---

### Post by CulleyS on 2007-10-22
Yeah, we seem to be having similar problems.

I've tested the built-in wav files with "aplay" and it's as if my surround speakers are simply unplugged.  When I play 5.1 files, I hear the left and right speakers as they should be.  

I checked my volume controls as well, they're all up.  But, there is simply no center speaker or sub.  When I play surround files as stereo, (or just stereo files) the sub and center speakers carry sound.  So, they're definitely plugged in, volume is up, and ALSA recognizes them.  It just seems that ALSA isn't working with surround.  Or, it's working, decoding the surround sound, sending it to the correct places, but nothing is coming out of the center or sub.  Or, if it IS, it's so so low, I can't hear it.

---

### Post by cogadh on 2007-10-22
In order to replicate the stereo signal across all 5 channels, you will need to create a custom .asoundrc file in your home folder. That file is not created by default as it is supposed to contain custom settings/configurations. ALSA handles audio differently than the Windows drivers do. Instead of automatically expanding a stereo signal to all speakers, it just uses the stereo speakers from your setup (i.e. the front two channels). If the audio source is formatted for 5.1 surround, then it will make use of all channels as it is required. Controlling the volume through the "Analog Front" control is the default (at least it has always been like that on my system with an SB Audigy LS), but you can change that by setting up a master volume control in the .asoundrc file. You should check out the ALSA Wiki page for more info on this:
[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

---

### Post by xjgnsdof on 2007-10-22
I don't have an .asoundrc file in my Home folder, so I created one. What do I put in it? That Wiki page you referred me to isn't very user-friendly.

Also, I only have "loop," "lp," and "fuse" in my /etc/modules file. I'm guessing that my Sound Blaster Audigy SE isn't among those listed.

---

### Post by CulleyS on 2007-10-22
[http://alsa.opensrc.org/index.php/Asoundrc](http://alsa.opensrc.org/index.php/Asoundrc)

You can look at this page.  It does require a bit of an understanding.  Like I said in my other thread, I tried doing this without much luck.  For one, many of the suggestions in there are for how to take a surround signal and push it through all speakers as if it were stereo.

Right now, ALSA is doing that.  I can hear stereo signals through all of my speakers (left, right, center, sub, etc.).  What I can't hear is the surround signal through all of my speakers.  When I play something that is 5.1 and play it as stereo, I hear all the parts through all speakers.  When I play something that is 5.1 and choose to play it as 5.1 (like I can do in VLC, for instance), I then hear the left channel bits, the right channel bits, but the other channels don't come through.  It's as if those channels get lost on the way to the speakers. :)  

I feel like I'm not being clear.  ALSA appears to be decoding and separating 5.1 info just fine, but no sound comes through my "surround" speakers.  I'd think the volume on those speakers was down, but as I already said, they sound off just fine with something that is in regular old stereo. 

Personally, I didn't see a solution to my problem in the asoundrc config settings.  You might have better luck, though.

I can't tell you what you need to put in your asoundrc file, though.  If I could, I wouldn't be having this problem. :)

---

### Post by cogadh on 2007-10-22
I'm in the same boat as CulleyS. I know what needs to be done, based on reading the wiki and such, but I don't really know how to do it, since ALSA has some of the worst user documentation I have ever seen. I have tried numerous customizations of my .asoundrc file, none of which have done anything useful. Once I figured out that the .asoundrc is not really required and that 5.1 audio files will actually play in 5.1 channels (in some cases, you might need to tell an application to use the ALSA pcm device "surround51" to make that happen), I just accepted that stereo files will just have to use the front two speakers only.

---

### Post by xjgnsdof on 2007-10-22
The ALSA docs are poorly organized, yes. I had surround sound in Gutsy before; there has to be a way to get it back. Let me know if you've heard of or tried anything that works.

Maybe somebody with working surround sound and Soundblaster Audigy card can post their .asoundrc file!

---

### Post by Libertine on 2007-10-22
This fixed the problem for me: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_and_test_surround-sound_speakers_.285.1_and_others.29_with_ALSA](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_and_test_surround-sound_speakers_.285.1_and_others.29_with_ALSA)

Hope it helps :)

---

### Post by xjgnsdof on 2007-10-22
Finally, something that works! Those Feisty Fawn instructions solved my sound card problem; I am getting glorious sound from every satellite in my 5.1 setup. I've used that unofficial Feisty guide so often for that version; I can't believe I didn't think to check it.

---

### Post by Libertine on 2007-10-23
Glad I could help :D

---

### Post by xjgnsdof on 2007-10-23
As a follow up question: why do I get no sound in Ubuntu when I had just booted into Windows. I restart, and everything's fine again.

---

### Post by cogadh on 2007-10-23
Still didn't help me at all (that's actually one of the things I already tried). I'm beginning to think there may be something seriously wrong with my sound setup. Probably my fault, I've done so many things to try and get all speakers working, I'm sure there is something still leftover from a previous attempt that is really screwing things up.

---

### Post by xjgnsdof on 2007-10-23
That solution doesn't exactly have perfect results for me. Whenever I boot into Windows, and then boot into Ubuntu, I get no sound in Ubuntu. When I reboot again into Ubuntu, then the sound blares from every satellite in my system. Any insights, anybody?

---

### Post by eheyl on 2007-10-24
I'm not sure where to put this but: I've got a soundblaster audigy value 5.1 and I get sound from my front speakers but no sound from the rear but I do get subwoofer action. Been looking around but am not sure what to do, if someone could help that would be GREAT. I'm solely into ubuntu 7.10

---

### Post by xjgnsdof on 2007-10-24
Start your own thread.

---

