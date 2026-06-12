---
title: "Problems with Bluetooth and Skype, curious situation"
date: 2013-03-30
forum: Networking &amp; Wireless
---

### Post by nicolamenicacci on 2013-03-30
Hi everyone, great to be here and write my first post.
I am quite active on the Italian forum, where I had a lot of support from great people, but I am encountering some problems with a couple of issues and received no answers. Here is the first:
After my cats ate all my wired headphones, I switched to a trust bluetooth headset (model 18214). When I paired it using my 2.1 bluetooth adapter, everything was working fine, with Skype as well. The only thing was that high fidelity listening had a lot of buffering and interruption and skype calls were possible only if I attached my face to the monitor (I have a desktop, the adapter is in the back, under a desk, but the distance is really short, max 4 feet if I move my head). I therefore decided to take a more updated version of bluetooth and decided to switch to Bluetooth 4.0 smart ready. I replaced it, paired my Apple Wireless Keyboard, my Apple magic mouse and all worked perfectly. I also paired my Trust headset with no problem but when I went checking with Skype, trouble began, to my great surprise, considering that the previous version, all things considered, worked and that hi-fi listening was going great this time.
To make a long story short, if I switch to HSP/HFP mode Skype becomes mute! If I set it to hi-fi listening, I can listen but not use the microphone.
No one in the Italian forum was able to help me, so i browsed the Internet to and fro and came up with some ideas.
The first one, which sound a little illogical to me, is that Bluetooth 4.0 does not support Skype (why then, am I able to listen incoming sounds in Skype using hi-fi mode?)
The second is that if I switch to a more recent version of Bluez this issue could be solved (but then shall I replace the current version and than make the package executable and so on, or shall I only install the new package which will automatically replace the old one?)
I also tried to work on the audio.config file, setting the audio.config file to "false" for the HFP/HSP options, like that
```
# Set to true to support HFP, false means only HSP is supported
# Defaults to true
HFP=true
```
switching it to
```
# Set to true to support HFP, false means only HSP is supported
# Defaults to true
HFP=false
```
No results.

Any ideas, hints and tips?
Greetings from a rainy Florence, Italy;

Nicola

---

