---
title: "annoying system beep"
date: 2008-04-30
forum: Multimedia Software
---

### Post by zenkaon on 2008-04-30
Hello, I have just installed hardy on several machines. Works brilliantly, however I now get an extremely annoying beep from the internal speaker whenever I get a new email in evolution or if I do a find in firefox which doesn't find anything.

This is unacceptable, sometimes I have to work in quite environments. I cannot stand computers making noise, unless its my own music. I have looked around the options and simply cannot find an option to turn off this incredibly irritating "feature". Hopefully this is just me, does anybody know where I should look?

How can I turn off the internal speaker in general? This has been unplugged at the motherboard for many years on my PC, but on a laptop its not that easy.

Does anybody know what /dev/ "what?" corresponds to the internal speaker? I'll happily point this to /dev/null.

This beep has to go, it's driving me and my colleagues mad.

---

### Post by hermes0710 on 2008-04-30
> **zenkaon said:**
> Hello, I have just installed hardy on several machines. Works brilliantly, however I now get an extremely annoying beep from the internal speaker whenever I get a new email in evolution or if I do a find in firefox which doesn't find anything.

This is unacceptable, sometimes I have to work in quite environments. I cannot stand computers making noise, unless its my own music. I have looked around the options and simply cannot find an option to turn off this incredibly irritating "feature". Hopefully this is just me, does anybody know where I should look?

How can I turn off the internal speaker in general? This has been unplugged at the motherboard for many years on my PC, but on a laptop its not that easy.

Does anybody know what /dev/ "what?" corresponds to the internal speaker? I'll happily point this to /dev/null.

This beep has to go, it's driving me and my colleagues mad.

In System > Preferences > Sound, on the last tab there are some options. Try changing them. (Do you have this sound when you are for example in a console and pressing backspace while you have written nothing?)

---

### Post by albeano2004 on 2008-04-30
^ What he said. You want to untick 'Enable System Beep' ;). Sounds awfully like what you described - an enabled system beep :)

---

### Post by zenkaon on 2008-04-30
Sorry guys, I should have said more on this.

In sound preferences, in the second tab "sounds" I have everything set to "No Sound", in the third tab "System Beep" I have everything unchecked.

I am still getting this annoying beep whenever I get an email or do a find in firefox, however not when I hit backspace in a terminal. I have everything set to mute and headphones plugged into my laptops socket. Man this thing is loud whenever I get an email, it's pissing everyone off in my office including me.

Does anybody know what /dev/??? the internal speaker is, I want to point this to /dev/null.

---

### Post by hermes0710 on 2008-04-30
> **zenkaon said:**
> Sorry guys, I should have said more on this.

In sound preferences, in the second tab "sounds" I have everything set to "No Sound", in the third tab "System Beep" I have everything unchecked.

I am still getting this annoying beep whenever I get an email or do a find in firefox, however not when I hit backspace in a terminal. I have everything set to mute and headphones plugged into my laptops socket. Man this thing is loud whenever I get an email, it's pissing everyone off in my office including me.

Does anybody know what /dev/??? the internal speaker is, I want to point this to /dev/null.

Try removing the module:

```
sudo rmmod pcspeaker
```

---

### Post by Cannaregio on 2008-04-30
[COLOR="#0000ff"]EITHER[/COLOR] you recompile alsa yourself
[COLOR="#0000ff"]OR[/COLOR] you open your boxes and unplug the internal speakers
[COLOR="#0000ff"]OR[/COLOR] you install the Gnome ALSA mixer: there will be a slider for "[COLOR="Blue"]Master M[/COLOR]" along with usual "master". 
If you now mute "Master M" you'll nuke the internal speaker, not the external.

Good luck

---

### Post by GingerAlex on 2008-04-30
I fear the plot may be thicker than you suggest, I have had the same issue since installing Hardy Heron.

I tried to disable this from within Evolution. However in the Evolution preferences tabs, there is now nowhere to set Notification preferences in Evolution, which, as I recall, used to allow the controlling of beeping on new mail. *The help file seems to suggest this section of the options is still there.*

I too would like to be free from beeping email, but I don't see why this should be at the expense of beeps where they are relevant, such as low battery warnings etc. Plus it appears from above posts that disabling system beep does not work in this case.

---

### Post by cor2y on 2008-04-30
You can try both these solutions if navigating to the sound settings in gnome and disabling system beep didn't work.
[http://tombuntu.com/index.php/2007/07/17/disable-your-internal-speakers-beep-in-linux/](http://tombuntu.com/index.php/2007/07/17/disable-your-internal-speakers-beep-in-linux/)
[http://ubuntuforums.org/showthread.php?t=126746](http://ubuntuforums.org/showthread.php?t=126746)

---

### Post by Whiffle on 2008-04-30
Actually: 

sudo modprobe -r pcspkr 

should get rid of it, and you can add pcspkr to the /etc/modprobe.d/blacklist file to get rid of it permanently.

---

### Post by zenkaon on 2008-04-30
Hey Whiffle,

Thats a very nice hack, what with the blacklist as well....I like it.

...ever considered becoming the Dread Pirate Roberts, my real name is Cummerbund....

---

### Post by not_surt on 2008-05-03
I've got the same problem in my Hardy install, however I don't want to remove the aural notification altogether but replace it with something more easy on the ears than the pc speaker.

I've tried explicitly picking a sound for every "system sound" in the sound preferences but to no avail.

---

### Post by planejason on 2008-06-03
Found the answer in this: [http://ubuntuforums.org/showthread.php?p=5106483#post5106483](http://ubuntuforums.org/showthread.php?p=5106483#post5106483)
post.  It is now a plugin that has to be managed with Edit-> Plugins.  Hope this helps.

---

### Post by Rivertold on 2008-06-03
You can also try 

sudo modprobe -r pcspkr

to disable the pc speakers completely.

sudo modprobe pcspkr  - to enable it again

---

### Post by foresto on 2008-06-03
Run this command in a terminal window:

  xset -b

Then read the man page for xset, especially the "-b" and "b" options.

  man xset

---

