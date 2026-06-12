---
title: "Remote key mapping, should be simple"
date: 2009-11-02
forum: Mythbuntu
---

### Post by ZedThou on 2009-11-02
My mceusb remote mostly works with mythtv, but I can't seem to customize the mapping of remote buttons to mythtv key presses. It seems like it should be simple. When I press the "Menu" key on my remote, the following is output by irw

```
$ irw
000000037ff07bdb 00 DVD mceusb
000000037ff07bdb 01 DVD mceusb
```So I try to map the Menu remote button to the key 'm' in mythtv with the following config in ~/.lircrc  but nothing happens. Any idea where I've gone wrong?

```

#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa 

begin
    prog = mythtv
    button = DVD
    config = M
end

```

---

### Post by joshoekstra on 2009-11-02
Got a me to here :S
Lirc is working with my Soundgraph-device, irw output is the same as the key I pressed. It's just mythfrontend that doesn't respond.
Mythfrontend looks in .mythtv/lircrc for the file which is a symlink to .lirc/mythtv, the mapping there is correct, but still mythtv doesn&#347; seem to like it.

You put the config in .lircrc, it's however best put in .lirc/mythtv

---

### Post by SiHa on 2009-11-02
I think you need a 'remote = mceusb' statement as the first line of the key definition.

Also, I agree with joshekstra. It's best to put it in the correct file. (~/.lirc/mythtv). Simpler as well, because you can just copy an existing definition and change the keys.

---

### Post by ZedThou on 2009-11-02
Thanks for the suggestions, I added the config entry to ~/.lirc/mythtv and now it's working. Don't know why I didn't think of doing that earlier!

---

### Post by joshoekstra on 2009-11-02
Good to hear, overhere I got lirc working somewhat as well, the frontend seems to respond to keypresses again after a upgrade to the latest mythbuntu-package. It seems to be updated today...

---

