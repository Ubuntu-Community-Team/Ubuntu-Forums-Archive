---
title: "Trouble with 'Play' Command from prompt"
date: 2011-02-24
forum: Multimedia Software
---

### Post by jmg158 on 2011-02-24
I was recently trying to use the play command from the terminal however I'm having difficulties. I'm getting the error message "play FAIL formats: no handler for file extension `mp3'" and I don't know why. Other programs such as rhythm box and banshee have no difficulty playing these mp3 files. 

Does anybody know more extensively what this error message is indicating? I suspect that I need to copy the mp3 codec from where it exists currently into the directory that is used by 'play' but I'm not really sure. I'm just honestly getting started and really wanted to learn how to play sounds/songs directly from the command prompt. 

Also, if a fix isn't obvious for this, does anyone know any better ways to play audio?

Thanks,
John

---

### Post by Chronon on 2011-02-24
Documentation about sox, rec and play here:
[http://sox.sourceforge.net/sox.html](http://sox.sourceforge.net/sox.html)

I'm not sure why it doesn't play though.  I just downloaded a song from jamendo and am using play to listen to it as I type this.

---

### Post by jmg158 on 2011-02-24
Okay, although I haven't had the opportunity to go through the entire site that webpage is very helpful.

It turns out that I am able to play .wav files but for some reason can't play mp3 files the same way.

While playing the .wav, I realized that I coudln't perform any other commands while it was playing. Is there any way to run this process in the background in any sense? Must I open up another terminal window if I want to execute other commands?

Thanks, and sorry for the questions which most probably seem simplistic.

---

### Post by Chronon on 2011-02-25
I am running Mandriva right now, so it's possible that the Ubuntu version has mp3 support disabled to avoid patent issues.  (I'm not sure if the restricted extras can be directly used by sox/play or not.)

Look into installing byobu.  It allows you to have multiple tabs in your terminal.  F2 creates a new instance and F3/F4 allow you to cycle through existing tabs.  It also can be configured to display IP address, temperature, CPU load, etc.  If you like to use the terminal it's a very useful program.  This would allow you to run play (or an MPD client, for example) and just spawn a new tab if you need to run a new task.

---

### Post by andrew.46 on 2011-02-25
Full mp3 support with sox can be enabled as outlined in this post:

[http://ubuntuforums.org/showpost.php?p=9859875&postcount=8](http://ubuntuforums.org/showpost.php?p=9859875&postcount=8)

Andrew

---

### Post by jmg158 on 2011-02-25
Thanks. you guys are collectively 'The Man'

Chronon, this will seem like a bizarre question, but is there a command that will open a new tab?

---

### Post by Chronon on 2011-02-25
```
byobu
```
to run byobu in your terminal.  (I think it's installed by default in Ubuntu.)

Then you can use F2 to create a new tab (or window as byobu's man page calls it) and F3/F4 will display the previous/next window.

---

### Post by jcline on 2011-04-11
Andrew's method of [http://ubuntuforums.org/showpost.php...75&postcount=8](http://ubuntuforums.org/showpost.php...75&postcount=8)
doesn't work for me on  Ubuntu 10.10.  Perhaps because the latest version of sox is 14.3.1 instead of 14.3.0, or more likely there were dependency problems (I think at the stage apt-get source sox) that I resolved in aptitude by keeping some packages at an older version.  The build fails at the step given in the attachment.  Any advice?

Actually I have solved this by first installing the appropriate mp3 decoding libraries
 
lame (3.98.4-0ubuntu1)
libmpg123-0 (1.12.1-3ubuntu1)
libmpg123-dev (1.12.1-3ubuntu1)
libtwolame-dev (0.3.12-1)
twolame (0.3.12-1)

Then I rebuilt sox directly from the sourceforge source (not ubuntu) and installed in /usr/local/bin.  It works if I prefix the command with padsp to compensate for the nonexistence of /dev/dsp.

---

### Post by andrew.46 on 2011-04-12
Actually that latest version of SoX is:

```

andrew@skamandros~$ sox --version
sox: SoX v14.3.**[COLOR="Red"]2[/COLOR]**

```

Seems like [a worthy upgrade]("http://sox.git.sourceforge.net/git/gitweb.cgi?p=sox/sox;a=blob;f=ChangeLog;hb=dd776a38ea4f86b31ef4464345dd3ce53d6af46a") as well. I build my won SoX directly from source as well, it is the best way to ensure you get every possible feature from this great application.

---

