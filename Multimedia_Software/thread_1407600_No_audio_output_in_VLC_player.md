---
title: "No audio output in VLC player"
date: 2010-02-15
forum: Multimedia Software
---

### Post by Sujit_Kumar on 2010-02-15
I installed Kubuntu 9.10 one week earlier and installed VLC player in it. But from that day VLC player is playing the video but not the audio. Please help. Also Banshee player is not playing any audio in Kubuntu.

---

### Post by Cabs21 on 2010-02-15
your sound card is working correct?  Try going into VLC preferences and adjusting the sound output modes.

---

### Post by fogelfink on 2010-02-15
I had something similar, because I have two sound cards.

Do you have several sound cards?  If so, you might simply be channeling the sound to the wrong output.

First check your sound preferences under system settings > mutimendia - here you can change the order of your sound devices.

What did the trick for me was to install the package 'padevchooser', use pulseaudio as my preferred sound output and manage where which application's sound is channeled to with the help of padevchooser.

good luck:D

---

### Post by Sujit_Kumar on 2010-02-16
I don't have multiple sound cards. In case of Banshee the player is simply not playing any song. Clicking any song shows a red cross to the left side of the song. And VLC is not giving any audio output. When played with dragon player the audio and video both come but not while playing with VLC.

---

### Post by Sujit_Kumar on 2010-02-18
Case Solved :- For VLC I had to install 'PulseAudio Sound Server' and change the output module driver to pulse audio. For Banshee I had to install 'ubuntu-restricted-extras'. Voila ! Everything is working now.

---

