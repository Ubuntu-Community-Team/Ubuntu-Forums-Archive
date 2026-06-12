---
title: "Creative HS-1200 Volume control"
date: 2011-02-22
forum: Multimedia Software
---

### Post by maito on 2011-02-22
Hello, 

I'm a happy owner of that headset and it works out-of-the-box in Kubuntu 10.04. However, there is something that could be better: Headset has volume up/down buttons and when I press button it turns volume up/down very nicely - but it controls default volume channel (my main loudspeakers on the table), not headset's own volume. I can control headset,s volume only from Kmixer volume slide for headset. 

How to configure sound system that I could adjust headset's (and only headset's) volume through its own buttons?

I noticed that when I plug in headset, /dev/input/event6 appears. If I cat /dev/input/event6 in terminal, I get some garbage on standard output while pressing volume buttons of the headset.

I guess I should be able to make some sort of keybinding between event6 and usb-audio-something but I'm totally clueless where to start. 

I would like not to make headset as a default sound device as I like to use main loudspeakers when watching film etc. Headset is mainly for skype.

Any help appreciated,

Henry

---

