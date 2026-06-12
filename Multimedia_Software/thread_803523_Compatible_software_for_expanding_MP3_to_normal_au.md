---
title: "Compatible software for expanding MP3 to normal audio"
date: 2008-05-22
forum: Multimedia Software
---

### Post by Ajarn Jack on 2008-05-22
I've got Gutsy/Gibbon and I'm looking for a music software program that I can install that would allow me to expand an MP3 to a normal (WAV or similar) file so that I can burn an audio CD and vice versa converting WAV to MP3.  Also, is there a software program available that will let me convert a FLAC file to MP3.  I've done all this before when I used Windows XP, but now I need to learn what is available and how to do it with this new operating system.

Any help with this matter would be much appreciated.

---

### Post by Akita on 2008-05-22
Soundconverter is probably the easiest and is GUI.

The VLC media player has a wizard (or command-line) mode that will convert formats for you.

Then there's mencoder, ffmpeg and a host of other command-line options.

---

### Post by cariboo on 2008-05-22
K3b converts on the fly when burning mp3 to audio cd. Make sure you have **libk3b2-extracodecs** installed or you'll get an error messages about missing codecs.

Here's a little script to convert from wav to mp3

 
```
#!/bin/bash 
# 
# wav2mp3
# 
for i in *.wav; do
    #out=$(ls $i | sed -e 's/.wav//g')
    #out=$(echo $i | sed -e 's/.wav$//')
    #lame -h -b 192 "$i" "$out.mp3"
    lame -h -b 192 "$i" "${i%.wav}.mp3"
done

```

Copy and paste the script in to a text editor and save the text to whatever name you want to give it then in a terminal type:

```
chmod +x "filename"
```

Next move it to /usr/local/bin so that you call use it in any directory:

```
sudo mv "filename" /usr/local/bin
```

NOTE: "filename" is the name you gave to the script, and of course hit enter and the end of each command. Make sure you have **lame** installed

Hope this helps.

Jim

---

### Post by Ajarn Jack on 2008-05-23
Thanks for all the help.  Since I'm new to Ubuntu 7.0 I don't have the knowledge yet to install a program like Soundconverter.  I've downloaded the package to my desktop and opened the file, but I don't know the commands to install it.  

Also I see that I should have LAME installed, but again I'm not sure where to look to make sure it was installed by the tech that installed Ubuntu.

Any help with these questions will start me on my way to using this audio program.

---

### Post by Lawrence Talbot on 2008-05-23
[http://packages.ubuntu.com/edgy-backports/all/soundconverter/download](http://packages.ubuntu.com/edgy-backports/all/soundconverter/download)

This link should give you a deb file that will install for you without any problems.  I think K3B is probably the best program to burn disc's  with, with Linux.

---

### Post by cariboo on 2008-05-23
There are a couple of ways to check if a program is installed. The easiest is to use synaptic, just click on search and type the program name. Synaptic will also automatically install programs for you instead of downloading them to your desktop. the other way to see if a program is installed is in a terminal type:

```
which "programname:
```

eg: 

```
jimk@alexis:~$ which lame
/usr/bin/lame
```

---

### Post by Ajarn Jack on 2008-05-24
Thanks for all your advice.  I used synaptic to install Soundconverter and I chose an MP3 to convert.  It converted it to an ogg file, but after burning that to CD it wouldn't play on my CD player.  How do I now change that file type to a regular WAV file that will play in a CD player?

Again, I very much appreciate anyone's comments that can help me turn an MP3 to a WAV file with this operating system.

---

### Post by cariboo on 2008-05-24
Use K3B it will automagically convert your mp3's to playable CD format. You don't have to convert anything yourself.

---

### Post by Ajarn Jack on 2008-05-25
Thanks for the advice Cariboo.  I've been to Williams Lake and onto Quennel Lake - very nice country.

I did manage to download the K3b program from Synaptic Manager and it did expand the MP3 to the K3b format, but that won't play in my CD player.

How do I convert this unplayable format (except in my computer) to a regular WAV type file?

---

### Post by Ajarn Jack on 2008-05-25
Instead of waiting for a response, I just started to get familiar with all the buttons on Kb3 and discovered how to choose the format to convert to.  I'd used the default of the ogg vorbis format initially, but found the WAV selection and it plays just fine.

Thanks for all the help!

---

### Post by Ajarn Jack on 2008-05-29
Since this experience with converting audio files from Mp3 to WAV using K3b I'd like to see if there is a way to convert FLAC files to Mp3 or WAV.  I didn't see that selection in K3b and wondered if there was another Linux program available for Ubuntu?

Thanks for all the help.

---

