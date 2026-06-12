---
title: "Sigh... Now I Don't Have Sound"
date: 2013-05-24
forum: Multimedia Software
---

### Post by CharleyGnarlyP290 on 2013-05-24
I just installed the newest batch of updates today. After it was finished I thought I would listen to a bit of music... Kraftwerk to be exact.
When I started up Rythmbox and hit play, the slider started moving (as if the music were playing) but no sound. 
Just yesterday after ripping the music to my computer it worked fine, now nothing.
Any help would be appreciated.

---

### Post by ohnonot on 2013-05-25
we would like to help you, but need more information.
start rhythmbox from a terminal, do you get error messages that look like they could be relevant to your problem?
what flavor of ubuntu? out of the box, or did you change things? what sound architecture? (pulseaudio most probably - is it initialising properly)

apart from that, it's sad if you can't listen to kraftwerk when you feel like it :-(

---

### Post by CharleyGnarlyP290 on 2013-05-25
I am running 12.04 out of the box. I don't tinker with the OS unless something needs to be fixed, like now. 
First, how do I open Rythmbox in the terminal?
How do I know if it's Pulseaudio?
I am really a bone head when it comes to the technical stuff in Ubuntu.
An Additional note: I get no sound whether it be internet, CD, or an audio player.

---

### Post by ohnonot on 2013-05-26
> How do I know if it's Pulseaudio?
is there a [task manager]("https://apps.ubuntu.com/cat/applications/precise/lxtask/") included in your install? open it and see if there's processes running that contain "pulse" in their names. if so, that's a good sign.
> An Additional note: I get no sound whether it be internet, CD, or an audio player.
so it's not rhythmbox related! good to know.
you still might want to try this:
> First, how do I open Rythmbox in the terminal?
1) open a terminal.
2) type "rhythmbox" (with two "h"!) and press return/enter.
rhythmbox should start normanlly now.
3) do whatever you do in rhythmbox to reproduce the problem.
now go back to the terminal window and look at the output that has been produced since you did 2).
4) copy it, paste it into your next post here.
5) put codetags around it (it's the #-sign on ubuntu forum text editor toolbar).

---

### Post by Yellow Pasque on 2013-05-26
```
rm -r ~/.pulse*
pulseaudio -k
```

---

### Post by gordintoronto on 2013-05-26
Run Sound Settings. Look for the sound being set Off or muted.

---

