---
title: "No sound in Rythmbox while other players work fine..."
date: 2009-07-12
forum: Multimedia Software
---

### Post by paparozoumis on 2009-07-12
Why is that?
What is it I can do to fix this and make Rythmbox play again?

In general, sound works fine on my computer except for this program. I hope you won't tell me not to use it :)

---

### Post by igorzwx on 2009-07-12
If you have Ubuntu 9.04,
your Rhythmbox should have the default Pulse,
as I remember.

Try System -> Preferences -> Sound
Change everything to Pulse

I cannot say more exactly, because I have already removed
this evil from all my boxes.

What will work for sure is to install Pulse control.
With this tool you can move the sound stream
where you want with one click of the mouse.

GOOGLE -> "Ubuntu PulseAudio howto"

---

### Post by vinutux on 2009-07-12
Delete all rhythmbox local configuration

**[COLOR="Red"]N.B you are lost everything of your playlist and library infos[/COLOR]**

Delete These folders

 **/home/yourname/.local/share/rhythmbox**

**/home/yourname/.gconf/apps/rhythmbox**

/home/yourname/.cache/rhythmbox

*[COLOR="YellowGreen"]yourname =your username[/COLOR]*


Then re-start rhythembox.... and check it

---

### Post by paparozoumis on 2009-07-12
> **igorzwx said:**
> If you have Ubuntu 9.04,
your Rhythmbox should have the default Pulse,
as I remember.

Try System -> Preferences -> Sound
Change everything to Pulse

I cannot say more exactly, because I have already removed
this evil from all my boxes.

What will work for sure is to install Pulse control.
With this tool you can move the sound stream
where you want with one click of the mouse.

GOOGLE -> "Ubuntu PulseAudio howto"



Yeap... It worked and now Rythmbox plays for good. 
I will have to check all the other programs to see if they still work, though
I will be back if I face any problems and you can take this as .... a threat :lol :lolflag:
Thanks anyway...

---

### Post by igorzwx on 2009-07-12
Interesting solution!

You may better type on terminal

gconf-editor

and fix the configuration.

Or edit other files.

And before deleting, you may better make a copy.

---

