---
title: "Strang sounds in Viber."
date: 2015-11-26
forum: Multimedia Software
---

### Post by kashan2 on 2015-11-26
Hello,

I am new here and new in Ubuntu as well.I am using Ubuntu 15.04 with acer E5-32NU. I have downloaded Viber and it is working. I have noticed that there are no output sounds. I went to setting and Audio&Video and change the audio output from built-in audio "HDMI" to built-in audio and now the sounds in working but in a really strange way. The notification sounds are bad. The ringtone as well. Everything is unfamiliar.

 I have checked the audio files in viber's folder and played them with VLC and they were normal. 

I don't know if that is happening because I have changed something else in somewhere else. 

I have removed the viber using sudo apt-get remove and install it again. Nothing happened. As I have mentioned, I am pretty new in this field. 


Ps: Skype audio is all normal.

---

### Post by kashan2 on 2015-11-26
Guys it's like a noise over the normal sound

---

### Post by ajgreeny on 2015-11-26
I don't know viber but there will probably be a configuration folder in your home, and removing the application itself will not remove or make any changes to that.

Search for that configuration and rename it as a backup, then try again with the viber application.

---

### Post by kashan2 on 2015-11-26
Thanks Ajgreeny. Ill give it a try and Ill come back.

---

### Post by kashan2 on 2015-11-26
Hello Ajgreeny. I haven't found that folder. Anyways. I went to Viber's folder. I switched the ringing.wav which is a normal ringtone with another file has the same properties. It wasn't an easy job, but after all, the song that I have switched the ringtone with it was noisy and unclear. The exact same noise that applies to the previous ringtone. Does that change anything?

---

### Post by kashan2 on 2015-11-27
Any suggestions guys?

---

### Post by ajgreeny on 2015-11-27
Not from me, I'm afraid.

Are there any Viber forums you can ask about this?

---

### Post by kashan2 on 2015-11-27
I have already looked up. There is no support for Linux from the company. Thanks anyway bro :)

---

### Post by kashan2 on 2015-11-27
Update!!!!
I have reached to a program called alsamixer. I chose my sound card and there were some charts and there were all maxed out. I have reduced the speaker thing to al green level and the sound in viber back to normal. The problem is, it keeps returning to the max status. How can I save the settings? What are these anyway? and what is the recommended setting "levels".

---

### Post by kashan2 on 2015-11-27
[COLOR=#333333][FONT=monospace]You have to modify the following line in /etc/pulse/default.pa[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]load-module module-udev-detect[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]with :[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]load-module module-udev-detect tsched=0


This is exactly what solved my problem.[/FONT][/COLOR]

---

