---
title: "Getting the MAudio Keystation88es recognised as a midi device by jack"
date: 2014-10-07
forum: Multimedia Software
---

### Post by nlaw on 2014-10-07
Having successfully configured ubuntu to run jack using Qjackctl and utilising the jack connect dialog to connect the jack virtual keyboard to Qsynth, I purchased a hardware midi keyboard, I was after a full sized, 88 key keyboard with weighted keys for practising the piano without driving everybody nuts (ie I can use headphones plugged into my laptop). Anyway with fingers crossed I plugged the keyboard into the USB port and with plenty of optimism expected to see the keyboard appear in the jack connect dialog. It appeared alright but not where I expected... it was under the ALSA section which was no good for feeding it's output into the qsynth. Eventually I found it necessary to have /usr/bin/a2jmidid -e & running. This mapped the keyboard from ALSA to MIDI and it then appeared under the midi section of the Qjackctl connect dialog. With it here I could now feed it's output into qysnth and under the Audio tab feed qsynth output into system. Here's the working configuration after having run /usr/bin/a2jmidid -e & Note under ALSA tab, although the keyboard appears in this section this isn't where you connect it to anything, the connection is made under the midi tab. Also note that it's necessary to expand the devices before you connect. This is because in my case only **a2j:keystation 88[20](capture):Keystation 88 MIDI 1** produces output so you highlight that output then click on qsynth:midi and then click connect. Don't forget to feed qsynth into system under the Audio tab. Hope that helps somebody from spending the hour I spent figuring this out.  

[ATTACH=CONFIG]257007[/ATTACH][ATTACH=CONFIG]257008[/ATTACH][ATTACH=CONFIG]257010[/ATTACH]

---

