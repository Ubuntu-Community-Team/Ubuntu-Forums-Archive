---
title: "[SOLVED] 7.10 Changes .lircrc not having effect"
date: 2008-03-27
forum: Mythbuntu
---

### Post by amphibem on 2008-03-27
OK I feel I am doing something silly here but which .lircrc should I be editing? I have a /etc/lirc/.lircrc and a /home/mythtv/.lircrc (that I have found?)

I have fiddled with both but the only change I have managed to effect is starting mythfrontend from the green button (I think is is 'Home') on the MCE2 USB remote. And I can't even remember that exact command now!

Can someone please point me to the file I should be changing, and possibly a link for possible configs?

P.s. What I am specifically trying to change is the behaviour of the channel +/-  buttons. They currently skip back/foward and I would rather they changed channel.

---

### Post by nasha on 2008-03-27
[HTML]http://www.mythtv.org/wiki/index.php/MCE_Remote#Example_lircrc_config_file[/HTML]

The above link will take you to a generic lircrc config, that may or may not work, no guarantees...

As for which one you should be editing ~/.mythtv/lircrc

---

### Post by amphibem on 2008-03-28
OK thanks. Just to be clear, when you say "~/.mythtv/lircrc" does that mean it is in my home folder? Ie to edit:

```
sudo nano /home/.mythtv/lircrc
``` ?

Got it cheers :)

---

### Post by nasha on 2008-03-28
```
sudo nano /home/username/.mythtv/lircrc
```

---

### Post by amphibem on 2008-03-29
Yer cheers, found it and finally managed some changes!

If anyone knows about dealing with multiple tuners.... [HTML]http://ubuntuforums.org/showthread.php?t=736877[/HTML]

---

