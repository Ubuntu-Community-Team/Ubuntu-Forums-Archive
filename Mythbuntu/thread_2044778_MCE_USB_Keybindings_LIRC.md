---
title: "MCE USB Keybindings LIRC"
date: 2012-08-19
forum: Mythbuntu
---

### Post by speed32219 on 2012-08-19
I am trying to setup the channel up and channel down on my mce remote to be PgUp and PgDown so I can page through the epg.    Maneuvering through the epg a channel at a time is slow and causes the audio to skip if I scroll to fast. I made the changes in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb and the channelup/channeldown function now does not work after changing it to PgUP/PgDown, so I know I am in the right place. Is there an interface/file within myth-frontend that needs my attention?

I took the info from the Mythtv keybindings document for remotes.  The kybd functions work. 

[http://www.mythtv.org/wiki/Keybindings#mythfrontend](http://www.mythtv.org/wiki/Keybindings#mythfrontend)

lircd.conf.mceusb entries 
KEY_PgDown        0x00007bec
KEY_PgUp          0x00007bed

Verified with irw, if I change back to original settings of channelup/channeldown they change a channel one at a time.

---

### Post by Lester_Burnham on 2012-08-20
Hi,

I would change it back to standard and instead make your changes in ~/.lirc/mythtv
Look for the section to do with the remote you have and find the entry for KEY_CHANNELUP and modify the config entry. 

begin
    remote = mceusb
    prog = mythtv
    button = KEY_CHANNELDOWN
    config = **Down**
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mythtv
    button = KEY_CHANNELUP
    config = **Up**
    repeat = 0
    delay = 0
end

Lester

---

### Post by speed32219 on 2012-08-20
Thank you, I looked in the hidden mythtv directory but couldn't find anything to do with keyboard/remote mappings.  Didn't even think to look in the hidden lirc directory, but exactly what I was looking for. Once again thank you.

---

