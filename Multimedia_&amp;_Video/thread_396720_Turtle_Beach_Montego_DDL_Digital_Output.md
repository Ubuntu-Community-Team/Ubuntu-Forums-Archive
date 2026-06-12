---
title: "Turtle Beach Montego DDL Digital Output?"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by ripple01 on 2007-03-29
Does anyone know how I can make my Turtle Beach Montego DDL soundcard output through the Digital Optical Out? I have my stereo setup that way, and I really hope there is a way to set it up so it will work. I'm really enjoying Linux so far and hope I can continue using it.

Cheers,
ripple01

---

### Post by ripple01 on 2007-03-29
Never mind, using the comprehensive guide that is stickied led me to Alsamixer and after fiddling with it for a few minutes I figured it out!

Cheers,

ripple01

---

### Post by hedgefighter on 2007-04-20
I have the same card, but I can't seem to figure it out. lspci says it's a C-Media Electronics card. I'm not sure if I need to install some drivers or what. Would you mind telling me what you did to get it to work?

---

### Post by hedgefighter on 2007-04-20
Haha, never mind. I didn't realize there were other columns off of the screen. I found the correct option <IEC985 0> at the end.

---

### Post by modestmelody on 2007-05-14
Not to bump an old thread, but the conclusion is that a Montego DDL works with ALSA through the digital optical out?  I'm considering going this way for a new card due to the great price and Linux compatibility is a huge requirement for me.

Also, does the card support DDL2.1, because that's what I've got at the moment...

---

### Post by hedgefighter on 2007-05-15
The specs on the card are here:
[http://www.turtlebeach.com/products/mtgoddl/indetail.aspx](http://www.turtlebeach.com/products/mtgoddl/indetail.aspx)

Everything, including the optical output, seems to work great with alsa. I even wrote a little shell script so I can switch the output from the analog to the optical and back with the click of a button - something I wished I could do in Windows.

Good Luck!

---

### Post by NoThanksM$ on 2007-09-03
Is there any chance you would be willing to post the script you wrote or send it to me offline?  I'd love to have that capability but don't know the first thing about scripting that sort of thing.

---

### Post by hedgefighter on 2007-09-03
Sure. It's pretty simple. It justs checks if the digital channel is on or off and mutes/unmutes it accordingly.

Throw the following in a file whatever.sh.

```
#!/bin/sh
condition=`amixer get "IEC958 Output" | grep "Mono: Playback [[]on[]]"`
if [ -n "$condition" ]
then
amixer sset "IEC958 Output" mute
else
amixer sset "IEC958 Output" unmute
fi
exit 0
```

Just make sure that your digital channel is named IEC958 Output. Then you can link a shortcut to:
```
sh whatever.sh
```

---

### Post by NoThanksM$ on 2007-09-03
Thank you VERY much!  Soon as I get the cable I'll be putting this to use often.

---

### Post by w00tfest99 on 2007-10-17
I'm sorry, I can't figure out how to get this to work as easily as you guys did.  I'm using ubuntu 7.10.  I went in to alsamixer and un-muted IEC958 but that didn't do anything.  Detailed instructions would be appreciated.

---

### Post by NoThanksM$ on 2007-10-17
Did you try the script posted above?  I haven't tried any of this on 7.10 yet, but the script works beautifully on 7.04.

---

