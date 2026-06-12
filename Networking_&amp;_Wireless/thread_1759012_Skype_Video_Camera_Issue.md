---
title: "Skype Video Camera Issue"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by hsl.gt7 on 2011-05-15
I m using Ubuntu 11.04 and my Skype version is 2.2.0.25,
Web cam I m using is Vimcro vc0301pl Camera when I installed new Skype after installing 11.04 my cam doesn't work it works finily with Chesse WEb cam Booth... any guesses how to fix it?

---

### Post by sanderd17 on 2011-05-15
So it works with cheese but not with skype?

If you execute
```

which skype

```

you should get the answer

```

/usr/bin/skype

```

If this is not the case, STOP going further and report the answer. If the answer is correct, you can proceed.

if you have 32-bit, do the following (please copy-paste to avoid typos):

```

sudo mv /usr/bin/skype /usr/bin/skype.original
sudo echo -e "#!/bin/bash \nLD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.original" > /usr/bin/skype

```

If you have 64-bit, execute
```

sudo mv /usr/bin/skype /usr/bin/skype.original
sudo echo -e "#!/bin/bash \nLD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.original" > /usr/bin/skype

```

Now, try to launch skype. If it doesn't work, reboot.

---

### Post by osfight.de on 2011-05-26
Worked for me, but my terminal does not like the ! before the /usr/bin and does not take the line

sudo echo -e "#!/bin/bash \nLD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.original" > /usr/bin/skype

as it is. Typing 

"sudo -s"

 first and removing the ! did work for me.

Thanks a lot, a [German version can be found here]("http://www.osfight.de/2011/05/ubuntu-11-04-skype-webcam-fix/").

R3s3t

---

### Post by sanderd17 on 2011-05-26
> **osfight.de said:**
> Worked for me, but my terminal does not like the ! before the /usr/bin and does not take the line

sudo echo -e "#!/bin/bash \nLD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.original" > /usr/bin/skype

as it is. Typing 

"sudo -s"

 first and removing the ! did work for me.

Thanks a lot, a [German version can be found here]("http://www.osfight.de/archives/1089").

R3s3t


Hmmm I don't know why he doesn't take the '!'.

You see what I'm doing? I'm just making a script with the text between the quotes (where \n is a new line). So my script is

```

#!/bin/bash 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.original"

```

and yours is

```

#/bin/bash 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.original"

```

the "#!" sign is a hint about what program should execute it (in this case /bin/bash). But the "#" sign is just a comment sign, but since /bin/bash is the default to execute scripts (at least in Ubuntu) it doesn't make a difference.




When posting that, I tried the 
```

echo -e "blablabla" > file.txt

```

command, but I didn't try the real command that I gave you (since I didn't wanted to screw up my skype installation :P )

---

### Post by osfight.de on 2011-05-26
It is obvious to me what you try to do, but not to my terminal :) 

If I do not remove the !, the terminal states

> bash: !/bin/bash: event not found. 

Executing it like this 

```

sudo -s
mv /usr/bin/skype /usr/bin/skype.original
echo -e "#/bin/bash \nLD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.original" > /usr/bin/skype
chmod +x /usr/bin/skype

```

does the job.

---

### Post by sanderd17 on 2011-05-26
Btw: it's a good site you have, I just learned something about the LaTeX plugin for inkscape. I use both: LaTeX and Inkscape, but I didn't know I could use LaTeX in Inkscape :P most of the time I use a picture made with inkscape in LaTeX.

---

### Post by sanderd17 on 2011-05-26
could you try if it works with single quotes instead of double?

I thought there was no difference, but I just read something on escapint the $ sign when echoing it, or as alternative, they say one could use single quotes.

I tried it with the "!" sign, and it worked.

---

### Post by jam365 on 2011-05-26
ive just tried this but its not working.

my webcam is 

D-Link DSB-C310 Webcam

and is recognised by cheese and kamoso but not by skype.

i'm a newbie so not sure what to do

can anybody help?


sorry tried this again and still not working in video options menu of skype (although i remember on maverick i had same problem but webcam worked in call)

did test call and built in mic is now working so assume webcam is too.

will test tomorrow when i can call someone... ( its 11.30 pm here)

---

### Post by osfight.de on 2011-05-27
> **sanderd17 said:**
> could you try if it works with single quotes instead of double?

I thought there was no difference, but I just read something on escapint the $ sign when echoing it, or as alternative, they say one could use single quotes.

I tried it with the "!" sign, and it worked.

The single ' solve the ! issue. Still, I need to sudo -s first.

---

### Post by jam365 on 2011-05-29
okay so much for thinking i had fixed this issue...

i have writen a script to launch skype with the following command: 

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.original 

which has fixed the video issue


thank u

however my built in mic on the webcam no longer works

it is: D-Link DSB-C310 Webcam

does anyone have any suggestions?

---

### Post by osfight.de on 2011-06-06
> **jam365 said:**
> okay so much for thinking i had fixed this issue...

i have writen a script to launch skype with the following command: 

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.original 

which has fixed the video issue


thank u

however my built in mic on the webcam no longer works

it is: D-Link DSB-C310 Webcam

does anyone have any suggestions?

Did you check that in the sound menu (Menu->System->Preferences->Sound) under input your D-Link is unmuted and selected?

---

### Post by jam365 on 2011-06-07
thanks for suggestion however i decided to bite the bullet and buy a new webcam. this one works perfectly straight out of the box.

---

