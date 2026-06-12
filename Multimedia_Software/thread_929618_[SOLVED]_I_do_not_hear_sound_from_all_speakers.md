---
title: "[SOLVED] I do not hear sound from all speakers"
date: 2008-09-25
forum: Multimedia Software
---

### Post by sowhat12345 on 2008-09-25
I install Ubuntu 8.04 on my new computer properly. I have 5.1 creative Inspire 5300 5.1 speakers and Creative 7.1 Audigy 2 sound card (and a onboard soundcard). I installed the drivers on Windows Xp , I can hear the sound properly. But I do not hear on Ubuntu. I could not find any drivers about my sound card in google. I try to change on preferences the options but it does not work. I just can hear the sound from 2 (front left and front right) speakers. I try it with 3 media players. Can someone help me :confused:

---

### Post by NT4usB on 2008-09-25
Have a look at this thread, see if it has some answers...
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by sowhat12345 on 2008-09-25
I did that : [http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/) 
Now my sound coming from all :) But it is very bad :( ????!!!!! :(

---

### Post by sowhat12345 on 2008-09-26
How can I understand if my sound card drivers are installed automatically ? Because sound is coming but it is scratchy ?!! :(

---

### Post by markbuntu on 2008-09-26
Since you already know how to edit your etc/pulse/daemon.conf file, try changing the deafult-sample-rate to 48000. I think that is what your card needs. If it does not work, you can always change it back.

---

### Post by sowhat12345 on 2008-09-27
markbuntu I did that you said. The sound got better , but still it is so bad that I can not listen to the music.

---

### Post by Buntuyang on 2008-09-27
"In 8.04, double click on the volume control, click on Edit/Preferences, then check External amplifier to be visible. The switches tab then appears. Uncheck External amplifier in that tab. Worked for me anyway." 
This really worked for me, I just installed ubuntu today and it took me 6 hours to get sound work.

post from [http://www.seopher.com/articles/how_to_fix_the_no_sound_in_ubuntu_7_10_on_a_laptop_or_notebook](http://www.seopher.com/articles/how_to_fix_the_no_sound_in_ubuntu_7_10_on_a_laptop_or_notebook)

---

### Post by sowhat12345 on 2008-09-27
Buntuyang thanks but I haven't got "External amplifier" in the sound settings. I change all devices but there isn't. I read the page which you gave me, maybe this option is for laptops or ubuntu 7. I don't know but  I'm sure that there isn't an option like this :( :(

---

### Post by markbuntu on 2008-09-27
Some cards sound terrible if the pcm slider in the mixer is above about 80%.

---

### Post by sowhat12345 on 2008-09-27
markbuntu I know that. Also I try it about 60 % but the problem is not still soft :( What should I do ? Where is not a way to solve the problem ?

---

### Post by markbuntu on 2008-09-27
Did you check the levels in the PA Volume Control and the sound mixer? Make sure the selcted device is your SB card and not the built in sound card. I think there is also a digital/analog switch box in the sound mixer for those cards and it must be unchecked for analog sound output.



I saw a thread where someone had a similar problem with sound working OK in windows but sounding very muffled in Ubuntu. What this person figured out was that he had his speakers in the wrong plugs. It worked OK in windows because windows figured our which plugs were being used and redirected the sound to them. Once he plugged the speakers into the correct speaker plugs, the sound worked great.

---

### Post by sowhat12345 on 2008-09-27
I had changed all my setting from the sound options. I don't know which is my device . I upload a screenshoot . Can you tell me which must be selected ?
[http://img392.imageshack.us/my.php?image=devicesre4.jpg](http://img392.imageshack.us/my.php?image=devicesre4.jpg)

After I selected the true option, I can tell you for other options ....

---

### Post by markbuntu on 2008-09-27
You have the correct one selected as far as I can tell, the CA106 should be your audigy card. Try turning all the levels down and see of the distortion goes away. What type of speakers do you have plugged into this?

---

### Post by sowhat12345 on 2008-09-27
I have 5.1 creative Inspire 5300 5.1 speakers and Creative 7.1 Audigy 2 sound card.

I upload a new screenshot my options for CA106 device.
[http://img264.imageshack.us/my.php?image=optionsms1.jpg](http://img264.imageshack.us/my.php?image=optionsms1.jpg)

Now can you tell me which are the truth options ?

---

### Post by sowhat12345 on 2008-09-27
Thank you so much !!! :) I did all the options 80% of mixer. And it gives great sound :) But it can not reac to windows quality . But no problem .. Thank you

---

