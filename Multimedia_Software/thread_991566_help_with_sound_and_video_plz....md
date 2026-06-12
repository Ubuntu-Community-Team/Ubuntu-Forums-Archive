---
title: "help with sound and video plz..."
date: 2008-11-23
forum: Multimedia Software
---

### Post by MaynardHSH on 2008-11-23
tbh this is my first week using ubuntu after a long time using windows xp so im really new at how to use the Terminal thingie :P
somehow when i use Rythmbox 0.11.5 some of the files play ok but at times it says that "Could not open audio device for playback. Device is being used by another application.", that for one, then whenever i try to watch videos at youtube or some other video site the frame rate is low, also sound messes up and i end up with none, i try the guide from ubuntu-reak and it works but when i reboot it comes back, i think i read somewhere i can like save certain changes so they apply every time i reboot or i start my pc. Also when im playing mp3's on Rythmbox and i try to watch videos the sound goes from the videos i really dont get it :confused: , i also read but didnt get a thing somewhere that said i can "play sound from diff apps at the same time" which confuses me since i've always play sounds from dif apps at the same time....or maybe it works different here :lolflag: 
btw my sound cars is a C-Media CMI8738 and since i installed the packages on the ubuntu-freak guide...i really have no idea whats wrong....any help appreciated :cool:

---

### Post by kostkon on 2008-11-25
> **MaynardHSH said:**
> tbh this is my first week using ubuntu after a long time using windows xp so im really new at how to use the Terminal thingie :P
somehow when i use Rythmbox 0.11.5 some of the files play ok but at times it says that "Could not open audio device for playback. Device is being used by another application.", that for one, then whenever i try to watch videos at youtube or some other video site the frame rate is low, also sound messes up and i end up with none, i try the guide from ubuntu-reak and it works but when i reboot it comes back, i think i read somewhere i can like save certain changes so they apply every time i reboot or i start my pc. Also when im playing mp3's on Rythmbox and i try to watch videos the sound goes from the videos i really dont get it :confused: , i also read but didnt get a thing somewhere that said i can "play sound from diff apps at the same time" which confuses me since i've always play sounds from dif apps at the same time....or maybe it works different here :lolflag: 
btw my sound cars is a C-Media CMI8738 and since i installed the packages on the ubuntu-freak guide...i really have no idea whats wrong....any help appreciated :cool:
Yes, this is the case of *Flash 9* not working well with *PulseAudio*.

You could check my instructions [here]("http://ubuntuforums.org/showpost.php?p=6222097&postcount=11") on how to remove *Flash 9* and install *Flash 10* which works better.

Hope that will solve your problem.

---

### Post by psyke83 on 2008-11-25
Kostkon is correct, but you need to do more than upgrade Flash 10. You also need to enable the PulseAudio ALSA plugins.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by MaynardHSH on 2008-11-25
> **kostkon said:**
> Yes, this is the case of *Flash 9* not working well with *PulseAudio*.

You could check my instructions [here]("http://ubuntuforums.org/showpost.php?p=6222097&postcount=11") on how to remove *Flash 9* and install *Flash 10* which works better.

Hope that will solve your problem.

ok thx for your response, i did all you said in your guide, and it somehow works but when im playing a mp3 on Rythmbox and then i try to watch a video on youtube it crashes, i push pause and all but still no sound and then no video, i can see like a steady image but it wont play, is there a way to undo everything? and make it again? to erase all of the changes and start from blank, cuze i seriously dont know what could be thats making this, and well i think it would be better to start on 0 than trying to find whats "that" thats making firefox and flash crash(or maybe there is a way :P ) 
or maybe you left it at that, without doing what psyke83 said??
i have no idea whatsoever....:confused: ....is there way to check if everything is "ok"? i know its not :p but maybe there is a way to know whats the problem or whats causing it?
thx in advance

---

