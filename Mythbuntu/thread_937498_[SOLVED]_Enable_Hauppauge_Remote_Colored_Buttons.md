---
title: "[SOLVED] Enable Hauppauge Remote Colored Buttons?"
date: 2008-10-03
forum: Mythbuntu
---

### Post by rschapman on 2008-10-03
I have a hauppauge remote that came with my 150 card. It has the TV, Videos, Music, Pictures, and Colored buttons on the bottom. How do I enable these buttons. I'm still a noob at a lot of this. Thanks for the help in advance. I tried searching around in the forums but may have missed something. If you can point me in the right direction I'd appreciate it.

---

### Post by SiHa on 2008-10-04
First, from a terminal window, run ```
irw
``` and press some buttons on the remote - namely the ones that aren't responding. That will at least show you if they are defined in your lircd.conf.

You should get something like: (for a key that works)
```
0x00001754 00 OK Hauppauge
0x00001754 01 OK Hauppauge

```

Ctrl+C to quit from IRW

If the buttons you need show up with IRW then they are defined, you just need to tell LIRC what to do with them in your **lircrc **file

With 8.04.01, you have two files:

```
/home/<mythuser>/.lircrc
```
and
```
/home/<mythuser>/.lirc/mythtv
```

The first should be a bunch of include statements pointing to the relevant configs in your .lirc directory.

**cd** to this directory and edit the mythtv file:
```
sudo nano mythtv
```

There is a definition for each remote button:

```
begin
    prog = mythtv
    button = OK
    config = Return
end

```

So you need to add an entry for each button that you want to use. the **button =** statement is the name of the button that IRW returns the **config =** is the keypress that you want to pass to Mythtv.

**Note**If you're using an earlier version of Mythtv, then I think you will just have a single file containing the key definitions for all the lirc applications. ```
/home/<mythuser>/.mythtv/lircrc
```

If, when you run irw you don't see the keys you want, the easiest way, I've found, is to simply record a new **lircd.conf** with irrecord. Post back here if you're stuck.

---

### Post by danbodoh on 2008-10-04
Here's how I defined mine in /home/<mythtvuser>/.lirc/mythtv:

```

####
# Added by dan bodoh
begin
   prog = mythtv
   button = Red
   config = D
end
begin
   prog = mythtv
   button = Green
   config = i
end
begin
   prog = mythtv
   button = Yellow
   config = Page Down
end
begin
   prog = mythtv
   button = Blue
   config = Page Up 
end

```

---

### Post by rschapman on 2008-10-05
Thank you very much. That's exactly what I needed. That is probably some of the best and most concise help I believe I've ever received in a forum. This is why I will continue to use ubuntu and its many derivatives.

---

### Post by SiHa on 2008-10-05
Glad to help. Feel free to click on the little medal at the bottom to say 'Thanks'. It's not compulsory though :D.

Also, if the poblem is solved, please go to Thread Tools > Mark as solved.

Cheers,

Simon

---

