---
title: "Kino has 1394 problem, doesn't list camera"
date: 2010-02-28
forum: Multimedia Software
---

### Post by charonred on 2010-02-28
I recently migrated to Karmic 9.10 from Hardy 8.04 and now I can't capture video from my JVC GR-DF470 Mini DV - it used to work in Hardy, but in Karmic the IEEE 1394 tab in Kino preferences doesn't list my camera (it lists nothing).

How do I get this working again - I didn't do anything in Hardy,the camera just worked.

---

### Post by charonred on 2010-02-28
after a bit of Googling, I found a fix [here]("http://ubuntufriends.wordpress.com/2008/06/25/kino-and-dv-1394-in-ubuntu-hardy/"); seems the later versions only give IEEE1394 access to root, not much good for ordinary users, so the trick is to change permissions.

Open Terminal and type:

```
ls /dev/raw1394 -l
```

This will then show the following (but with whatever the current date/time is)
crw-rw&#8212;- 1 root disk 171, 0 2010-02-28 15:10 /dev/raw1394

Now just change the permission to rw to everybody by typing the following;
```
sudo chmod 666 /dev/raw1394
```

then enter ```
ls /dev/raw1394 -l
```
which will then display the amended permissions
crw-rw-rw- 1 root disk 171, 0 2010-02-28 15:10 /dev/raw1394

now my JVC camera when plugged in is listed in Kino and I successfully captured the video from it :D

.

---

### Post by granny6989 on 2010-02-28
Thanks for that. Worked for me as well with a Sony DV camera.

S*

---

### Post by charonred on 2010-02-28
hmmm; seems the fix isn't permanent, and the script
```
sudo chmod 666 /dev/raw1394
``` needs running on each reboot

---

### Post by charonred on 2010-02-28
found a better fix

it appears Kino hasn't been updated or developed since 2008, but there appears to be a new application available to take it's place.

kdenlive 
seems to be a more powerful/configurable video editor and it works as soon as it is installed via Synaptic.

instructions are [here]("http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages") for different versions of Ubuntu

and it even works after a reboot - once camera is switched on and connected by firewire, open kdenlive and go to 'Monitor' and tick/check 'Record Monitor'; this opens a new dialogue  window, click the 'Connect' button

---

