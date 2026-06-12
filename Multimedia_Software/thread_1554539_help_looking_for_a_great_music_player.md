---
title: "help: looking for a great music player"
date: 2010-08-16
forum: Multimedia Software
---

### Post by fatalfix on 2010-08-16
good day everyone..
Im an ubuntu user..
Ver 10.04 lucid lynx..

Im liking ubuntu, but i have troubles with my music..

I always transfer my music to other storage deveices(flash drives) using winamp in windows..but i cant do it with rythmbox..i cant run winamp in ubuntu well using wine.
Is there a music player that can do the job for me..?

My other problem is that, the audio quality in ubuntu is not that great unlike in windows..is there any sound enhancer in ubuntu..?.

---

### Post by slooksterpsv on 2010-08-16
> **fatalfix said:**
> good day everyone..
Im an ubuntu user..
Ver 10.04 lucid lynx..

Im liking ubuntu, but i have troubles with my music..

I always transfer my music to other storage deveices(flash drives) using winamp in windows..but i cant do it with rythmbox..i cant run winamp in ubuntu well using wine.
Is there a music player that can do the job for me..?

My other problem is that, the audio quality in ubuntu is not that great unlike in windows..is there any sound enhancer in ubuntu..?.

You should try Songbird, you can get it from [http://getdeb.net/](http://getdeb.net/) but you have to install their repositories first, go here to install the repositories: [http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb](http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb)
And here to install songbird after getting the repositories: [http://www.getdeb.net/install/songbird/1.4.3-1%7Egetdeb2](http://www.getdeb.net/install/songbird/1.4.3-1%7Egetdeb2)

I think there's an updated version elsewhere... let me try to find it real quick...

EDIT:

Found it: [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

---

### Post by rp88 on 2010-08-16
I've got to disagree about songbird. I used to use it and loved how it replaced itunes and kept a nice looking interface but it was SO SLOW and integration into linux wasn't that great. Also they dropped support for linux about 5 months ago. I switched over to banshee about 2 weeks ago and i think its a lot better then songbird in terms of speed and integration.

With banshee you can sync MTP devices, Mass storage devices, Rio Karma devices, and iPods (except touch/iphone)

---

### Post by ccc2007chaos on 2010-08-16
> **fatalfix said:**
> good day everyone..
[...]
My other problem is that, the audio quality in ubuntu is not that great unlike in windows..is there any sound enhancer in ubuntu..?.

I have to say some things about Ubuntu. The sound part of course.

Ubuntu plays what it gets from a file or whatever source thru the sound card that's installed on your computer. Well, this might seem simple but... The build in sound cards have poor quality. Generally, the human ear can hear from about 20Hz to 20kHz. Why am I telling this? Because, the cheap sound cards can play until about 15kHz but this varies for each sound card. From that frequency and until the limit of frequency depending on the sampling rate, these frequencies are added in your signal. This is called aliasing. On Windows, there are some algorithms that "fix" this problems. The truth is that there are some filters that cut off the frequencies above some limits. This can be achieved on Ubuntu with an EQ, but this is not the best you can do. You might use the built in EQ that comes with the program you use.

Generally, there are many plug-ins that can be connected with your music player program. This is one of them [http://www.linuxdsp.co.uk/download/gr_eq2/index.html](http://www.linuxdsp.co.uk/download/gr_eq2/index.html) and as you can see there is one fader that can amplify or reduce the level of an area with center frequency is 16kHz. That will reduce the quality. Another plug-in is [http://www.linuxdsp.co.uk/download/ch_eq1/index.html](http://www.linuxdsp.co.uk/download/ch_eq1/index.html) .

I really don't know what you mean by audio quality and it's a really nice subject to discuss about and to make it more specific.

Hope the information given are useful.

---

### Post by fatalfix on 2010-08-17
wow..thanks for such replies..

I also used songbird before but they stop support in ubuntu..

What do u think about guadeque player..?is it good..?

Im just using a netbook..so hardware is not good..is there a lightweight player that can do syncing through flash drives..?but also good in music management..


What i mean about sound enhancer is that in windows, im using srs sandbox to enhance my audio..is there a software like that in ubuntu..?

Thanks for your reply guys..

---

### Post by ccc2007chaos on 2010-08-17
Audacious has many plug-ins. Try it. If you are searching for more, you can go here [http://linux-sound.org/](http://linux-sound.org/) but that's quite deep! :D

---

### Post by cchhrriiss121212 on 2010-08-17
I'd recommend using Quod libet, it is light enough for a netbook and has loads of plugins to use. For transferring files I would just use the file manager.

---

### Post by hankaaron88 on 2010-08-17
I would say that Banshee is the way to go. It's a music and movie player, which I tend to stay away from, but I haven't had any real problems with it to date.

---

