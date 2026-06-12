---
title: "simple notes about headset"
date: 2009-05-23
forum: Multimedia Software
---

### Post by Claus7 on 2009-05-23
Hello,

I would like to share my experience with the headset that recently came to my possession. What I wanted to do is to make them work normally under various conditions in jaunty, which at the beginning was not so straightforward to me (it is now=D>!).

The type of headsets in question are Logitech ones. They come with one cable having two cords in the end, which can be attached to a sound device and/or with a usb expansion cable, which allows the headset to become a usb device. 

[LIST]
[*] Sound card
In order to hear sound from your headset from a soundblaster sound card, then:

[LIST=1]
[*] you remove the cables of your speakers (normally two) from your sound card and you attach the one cord of your headset to where the one of the two cords of the speakers were attached and the other to the socket of the microphone. 
[*] you leave the speakers untouched and you plug the headset to one free socket (that way I could here sound only from one channel of my headset).
[/LIST]

With the above configurations you do not have to change anything from your ubuntu sound configuration and in the i-2 case you can have sound both from your speakers and your headset. That means that always here, the default device is your sound card of choice.


[*] usb option
You attach the usb expansion and you use your headset as a usb device. This configuration is entirely different than before. That way you cannot have sound from your headset, unless you change from sound settings the default sound card to your headset option (if your headset is recognized as a device, the new options will appear in every sound menu). 
Skype can be used with this configuration only if you go in the settings of it and set as sound device your headset. Have in mind that if you remove your headset from the usb slot, skype might complain with an error if you try to make a call. So you have to revert its options back to your sound card. Also for the options to appear it is better to plug it when skype is not launched[/LIST]

Regards!

---

### Post by Claus7 on 2009-11-09
Hello,

in step 2 of the previous post, I have to say that in karmic things are working pretty nicely: I can hear sound from both of the channels.

Regards!

---

