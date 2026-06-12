---
title: "Flac and monkey audio (ape) vs amarok"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by blackmh on 2006-09-30
Couple months ago when I installed kubuntu flac files worked out of box IIRC but now I get "There is no audio channel" error no matter what output plug-in is seleceted (alsa,oss). Amarok is using xine engine and and all packages concernig xine are installed except xine-dev. 

Also, I'd like to know if its possbile to make amarok play ape files. After a quick google search I couldn't find anything relevant.

Thanks in advance!

---

### Post by tdn on 2008-04-20
I would also like to know how to play APE files.

Or more interesting -- How do I convert .APE files to a non-proprietary format like FLAC or ogg?

---

### Post by edm1 on 2008-04-20
It's not easy but if i end up with ape files i use 'libjmac-java' to convert them to wav files then my ordinary transcoder 'Perl audio converter' ([available here]("http://linuxappfinder.com/package/pacpl")) to transcode them to whatever.

To install libjmac-java (which runs under J2SE)
```
sudo apt-get install libjmac-java
```

Then to convert a ape file to wav
```
java -jar /usr/share/java/jmac.jar d INPUT_FILE.ape OUTPUT_FILE.wav
```

---

### Post by tdn on 2008-04-20
```

~ $ sudo apt-get install libjmac-java
[sudo] password for tdn:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libjmac-java

```

---

### Post by edm1 on 2008-04-20
Sorry i didnt realise it was only in the Hardy repositories. I'm not sure of an alternative, maybe a good reason to update to hardy when it's released later this week.

---

### Post by tdn on 2008-04-20
Do I need to add a special source to my sources.list?

Here is my sources.list:

[http://thomasdamgaard.dk/paste/P1118.html](http://thomasdamgaard.dk/paste/P1118.html)

---

### Post by tdn on 2008-04-20
Okay. I will reinstall when Hardy is released. I do not feel that the upgrade procedure is safe yet. I have tried to upgrade on every release since 5.10, but every time something has been failing. Often resulting in something not working correctly after the upgrade.

---

### Post by disturbedite on 2008-04-20
just install soundkonverter, its great.  audacious supports monkeys audio files as well.

---

### Post by tdn on 2008-04-23
> **disturbedite said:**
> just install soundkonverter, its great.  audacious supports monkeys audio files as well.

Well... soundkonverter does not support APE. Why should I install this?

---

### Post by disturbedite on 2008-04-24
> **tdn said:**
> Well... soundkonverter does not support APE. Why should I install this?
bullcrap it doesn't support MA.
soundkonverter itself isn't a conversion program, it is simply a frontend end to various programs.
you just prolly don't have the MA package installed.  it is available in the rarewares or debian-multimedia repos.  (although, of the two, the debian-multimedia repo has the newest version).

---

### Post by Neovos on 2008-05-06
So soundconverter (gnome) supports the plugins that gstreamer supports. ok. So when I search the repositories for any type of APE plugin, can't find one. So I go here: [http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/](http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/) and install that one. It works under Hardy no problem in the command line. But the real question is how do I get gstreamer or soundconverter to use it? Can I make custom plugins for gstreamer? Sound converter just shows up with the default 4 options.

---

### Post by process91 on 2008-05-12
I used the mac CLI to decompress all the ape files into flac files like this:

```
mac "01 - Audio One.ape" "01 - Audio One.flac" -d
```

Then, of course, they will play in any gstreamer app or Amarok or anything else that can understand FLAC (make sure you have the flac package installed)

---

### Post by edm1 on 2008-05-12
> **process91 said:**
> I used the mac CLI to decompress all the ape files...

Where did you get 'mac' from? Perl audio converter can use it but i was unable to find it.

---

### Post by process91 on 2008-05-12
You can get the mac CLI from here - 
[http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/](http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/)

Actually, the mac CLI will only convert to wav. So you could use it to do this
```
mac "01 - Audio One.ape" "01 - Audio One.wav" -d
```

And then use any other program like soundconverter (sudo apt-get install soundconverter) to convert the wav files to FLAC.

---

### Post by e630193 on 2008-06-01
> **tdn said:**
> I would also like to know how to play APE files.

Or more interesting -- How do I convert .APE files to a non-proprietary format like FLAC or ogg?

Did you get this sorted? If not, I can probably help as I store all my music is ape format, convert to flac (using a perl script that I wrote) and play them in Amarok.

Let me know if you need details.

---

### Post by misterspider on 2008-07-22
> **e630193 said:**
> I store all my music is ape format, convert to flac (using a perl script that I wrote) and play them in Amarok.

Can i ask why you do it this way? Whats the benefit of storing in ape and playing in flac, why not just store the flac?

---

