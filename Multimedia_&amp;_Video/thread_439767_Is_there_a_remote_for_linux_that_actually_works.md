---
title: "Is there a remote for linux that actually works?"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by hotani on 2007-05-11
I have finally had enough of the constant failing of my ATI Remote Wonder. It works for a while, then stops. Not all the keys are functional. I constantly have to fart around with text files to get it to cooperate. There is no way to get it to do something different for two applications. When it craps out, I have to run a command line fix to get it working again. Sometimes that does the trick, sometimes not. I have found the best place for my remote was the frakking trash can.

My question is this: Is there a remote that will work in linux without the headaches listed above? Because the last one made me want to rip my eyeballs out. Something different that actually works and doesn't cause hours of frustration would be wonderful.

---

### Post by dfreer on 2007-05-11
I really like the little remote that comes with HP laptops, because all of the keys on the remote are mapped to actual keypresses on the keyboard (Cancel = backspace, Ok = Enter, Up/down/left/right = keypad up/down/left/right etc). Volume up/down/mute work out of the box, and everything else (except 2 keys that deal with quickplay) can be mapped in any media program that supports mapping WITHOUT having to deal with lirc. some defaults can be mapped in System > Preferences > Keyboard Shortcuts. why can't most remotes be this way? 

sorry, though, this probably won't help you much since you would need to buy a HP laptop to use the remote, but maybe if you are in the market in the near future it might :p

---

### Post by bowmanr on 2007-05-11
Hi,

Never had any issues with my i2c remote (came with my one of my Haupauge PVR-350 cards) -- used on master backend/frontend. An option, but expensive.

Alternatively, you could try something like a standard serial remote sensor from this (UK based) site  <<http://www.gibbsdesign.co.uk>> (product page : <<http://www.gibbsdesign.co.uk/products/sir/sir.html>>). A little fiddly, involving compiling lirc_serial with the igor(?) mods. I've used one of these with success on my remote frontend, however, it was a little effort to make it work, not straight out of the box like the i2c. Also, it is necessary to have available an IR remote, I use the one from my old DVD recorder.

Some food for thought maybe.

Regards
Robert

---

### Post by williammanda on 2007-05-11
I use the firefly radio freguency. Here is the post that has all my info I went through to get it to work:
[http://ubuntuforums.org/showthread.php?p=2424848#post2424848](http://ubuntuforums.org/showthread.php?p=2424848#post2424848)

This may look like a lot but I was learning about lirc at the time too. I have gotten it down pretty easy now. I just got through installing feisty and it took me about 15 minutes to get lirc working with my remote. I love the remote.

Let me know if you need any assistance.

Thanks

---

