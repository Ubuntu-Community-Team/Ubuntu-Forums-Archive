---
title: "Frequency Generator?"
date: 2009-08-05
forum: Multimedia Software
---

### Post by tomasrey88 on 2009-08-05
Hi, 

There are free DOS programs that can be used to generate frequencies. You input the Hz frequency(s), sine or square wave, output cycle (on for x seconds, off for x seconds, on again, etc), and the computer will generate audio output. I use this audio output for scientific research. I cannot find any programs in Linux to do so. In Windows, there are dozens of programs, some of which are free. For example, you can use Winamp in Windows. 

Here is a list of such free programs to give you an idea of what I'm looking for, except for Linux: [http://www.introductiontorife.com/pmr1.html](http://www.introductiontorife.com/pmr1.html)

What computer programs for Ubuntu Linux can you use to generate audio frequencies? 

Thanks,
:P

---

### Post by dusanyu on 2009-08-05
siggen may do what you need 
[http://linux.maruhn.com/sec/siggen.html](http://linux.maruhn.com/sec/siggen.html)
[http://packages.ubuntu.com/intrepid/siggen](http://packages.ubuntu.com/intrepid/siggen)

---

### Post by xzero1 on 2009-08-05
You can do frequency selectable sine and pink wavs using speaker-test.

---

### Post by mcduck on 2009-08-05
Audacity also has a sound generator (sine/sawtooth/square, you can set the frequency, amplitude and length), and of course there's a wide selection of software synths and plugins available which will pretty much allow you to generate any waveform you want as long as it's in audio range..

I'm pretty sure I've also seen some frequency generators made for scientific use in either "Scientific" or "Electronics"-sections in the repositories. Have you tried searching with Synaptic?

---

### Post by tomasrey88 on 2009-08-06
siggen looks like what I need, however, I cannot locate it in synaptic. I cannot locate it in add/remove programs. I also cannot add them as a new software source because I do not know the APT line and key file of siggen. Please advise.

I have the same problems mentioned above with speaker-test. Please advise.

Thanks,
:P

---

### Post by mc4man on 2009-08-06
[http://packages.ubuntu.com/search?searchon=names&keywords=siggen](http://packages.ubuntu.com/search?searchon=names&keywords=siggen)

Will install in hardy also (I installed the jaunty version (all the same I believe, only diff is name

Note that packages.ubuntu has been having some issues lately, if you get a blank page at any point then reload (refresh) or retry (arrow back

---

### Post by dusanyu on 2009-08-06
siggen  is in the Universe repo. or you can use this direct link to download the repo. 

[http://mirror.mcs.anl.gov/pub/ubuntu/pool/universe/s/siggen/siggen_2.3.10-1_i386.deb](http://mirror.mcs.anl.gov/pub/ubuntu/pool/universe/s/siggen/siggen_2.3.10-1_i386.deb)

---

### Post by roaldz on 2009-08-06
> **dusanyu said:**
> siggen  is in the Universe repo. or you can use this direct link to download the repo. 

[http://mirror.mcs.anl.gov/pub/ubuntu/pool/universe/s/siggen/siggen_2.3.10-1_i386.deb](http://mirror.mcs.anl.gov/pub/ubuntu/pool/universe/s/siggen/siggen_2.3.10-1_i386.deb)

I think you mean ¨download the package¨ a repo contains packages.

---

### Post by tomasrey88 on 2009-08-07
i figured it out. it is not available for hardy. siggen is only available for jaunty, karmic, and intrepid. i will try to resurrect an ancient laptop and see if i can get it to work with jaunty. thanks.

---

### Post by Mia1990 on 2009-08-07
Does anyone know if they will make the sounds that drives dog's away i would like to make that sound and put it on my mp3 player so i will have it when i go walking i was about bitten by a dog tonight.

---

### Post by mc4man on 2009-08-07
> figured it out. it is not available for hardy. siggen is only available for jaunty, karmic, and intrepid. i will try to resurrect an ancient laptop and see if i can get it to work with jaunty. thanks.

Well it's your choice, but as mentioned there is absolutely nothing preventing you from installing any of those 3 versions on hardy. 

The dependencies for all 3 are exactly the same (libc6 >= 2.7, libncurses5 >=5.6+20071006-3 )  Hardy's libc6 is 2.7 and the libnurces is also available from the hardy repo (note that the libncurses version is from 2007

It's the exact same app, pick any of them, it will install and work fine on hardy (have done so here

---

### Post by roaldz on 2009-08-07
> **Mia1990 said:**
> Does anyone know if they will make the sounds that drives dog's away i would like to make that sound and put it on my mp3 player so i will have it when i go walking i was about bitten by a dog tonight.

I´m, sorry but that won´t work I think, unless your mp3 player supports a format that supports frequencies above 20Khz, and than your mp3 player´s DA-converter (which makes the sound) has to support this too. The samplerate must be high enough too, at least double the hearing frequency. A dogs ears can hear up to 60 Khz, far above a humans ear.
Is there actually a frequency that drives dogs away?

Roald

ps. I´m not shure if you´re serious, but I´m responding anyway:)

---

### Post by crazyfuturamanoob on 2009-08-07
> **tomasrey88 said:**
> siggen looks like what I need, however, I cannot locate it in synaptic. I cannot locate it in add/remove programs. I also cannot add them as a new software source because I do not know the APT line and key file of siggen. Please advise.

I have the same problems mentioned above with speaker-test. Please advise.

Thanks,
:P

If you can't find something in Synaptic, then you can't install it using apt-get, because Synaptic is a front-end for apt-get. You might need to manually add new repositories to be able to install a certain packages in Synaptic/apt.

But you use apt-get like this:
```

$ sudo apt-get update
$ sudo apt-cache search <keyword>
$ sudo apt-get install <packagename>

```

[quote=roaldz]
Is there actually a frequency that drives dogs away?
[/quote]
Yes. I visited once a slaughterhouse. I could smell roasted meat everywhere. When I asked why there are no animals drooling at the gates, they told me they got a ultrasound thing which drives the animals away.

---

### Post by roaldz on 2009-08-08
> **crazyfuturamanoob said:**
> If you can't find something in Synaptic, then you can't install it using apt-get, because Synaptic is a front-end for apt-get. You might need to manually add new repositories to be able to install a certain packages in Synaptic/apt.

But you use apt-get like this:
```

$ sudo apt-get update
$ sudo apt-cache search <keyword>
$ sudo apt-get install <packagename>

```


Yes. I visited once a slaughterhouse. I could smell roasted meat everywhere. When I asked why there are no animals drooling at the gates, they told me they got a ultrasound thing which drives the animals away.

Then i´m curious about how to use it in a ¨live¨ situation using your mp3 player:P

---

### Post by crazyfuturamanoob on 2009-08-09
> **roaldz said:**
> Then i´m curious about how to use it in a ¨live¨ situation using your mp3 player:P

You can't download music with APT nor Synaptic.

---

### Post by roaldz on 2009-08-10
> **crazyfuturamanoob said:**
> You can't download music with APT nor Synaptic.

Sorry, forgot to only quote the last part of your post.

---

### Post by crazyfuturamanoob on 2009-08-10
Found this, 18000Hz noise, gives me a headache and makes my ears hurt: [http://lm2005.googlepages.com/highfreq1.mp3](http://lm2005.googlepages.com/highfreq1.mp3) Go find out if it has any effect on dogs and tell me if it works. :P

I also generated some noise with audacity and raised pitch to 20000Hz but it's still working on it, using 100% of my second CPU. Will post that thing as soon as it is complete.

---

### Post by markbuntu on 2009-08-11
You will need a speaker that can reproduce that frequency with a lot of decibles and there are not many that can do that.

---

### Post by crazyfuturamanoob on 2009-08-12
Many people don't hear 18-20KHz frequencies so they might work as well.

---

### Post by mcduck on 2009-08-12
> **markbuntu said:**
> You will need a speaker that can reproduce that frequency with a lot of decibles and there are not many that can do that.

Yes, the speaker will be a bit of a problem but that at least is relatively easy to fix, as such speakers are actually sold even for consumer market.

The actual showstopper would be finding a portable audio player that both supports a format that is capable of storing such high frequencies, and is also able to play them..

---

