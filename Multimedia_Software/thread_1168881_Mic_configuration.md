---
title: "Mic configuration"
date: 2009-05-24
forum: Multimedia Software
---

### Post by AboSamoor on 2009-05-24
I am trying to get my mic working. I can not record using the mic.

The first time I tried to configure the mic it succeeded by removing pulseaudio. After two weeks I lost the recording functionality again even I did not make any change. 

I am trying again to fix the problem, and after 4 hours of searching, I made a mess in the system, I have many switches and options in the volume control and I tried many options in the alsa-base conf file.

I want your help to:

1- Restore the configuration of ubuntu as a fresh install 
2- Diagnosing procedure to determine the problem.

My system:
[http://www.alsa-project.org/db/?f=0f822b00b78d14f303a217ee64ba210390b0a49a](http://www.alsa-project.org/db/?f=0f822b00b78d14f303a217ee64ba210390b0a49a)

---

### Post by miegiel on 2009-05-24
Most sound cards have 2 mic inputs, make sure you've selected the right 1 in the *Volume Control* panel (options tab on my machine).

---

### Post by AboSamoor on 2009-05-24
I tried both of the inputs and options, the problem that I don't know which is for which ?

---

### Post by miegiel on 2009-05-24
I used the "test" button in System > Preferences > Sound to test the mic input and switched to *Mic2* on the options tab in the *Volume Control* panel.

But it could also be that you have selected a wrong input to capture (see *Volume Control* switches tab).

---

