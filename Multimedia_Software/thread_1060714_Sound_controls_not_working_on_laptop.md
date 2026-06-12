---
title: "Sound controls not working on laptop"
date: 2009-02-05
forum: Multimedia Software
---

### Post by joelwhrs on 2009-02-05
I have a dell inpirion e1505 and my volume controls on the front and on the keyboard dont work. They used to work great but then all of a sudden they just dont work. it still works as long as i adjust it manually using the volume control. and while i'm asking this i might as well ask how to get all my system sounds working correctly, everytime that i get to where a curser cant move i get this annoying beep, exactly the one that happens when windows has an error like a virus or something, scares me everytime lol:p

---

### Post by joelwhrs on 2009-02-06
If it helps when I adjust the sound using the controls it will actually adjust the capture volume and not the main volume.

---

### Post by joelwhrs on 2009-02-09
I just checked and the controls work if i go on another profile. PLEASE help i cant turn down that annoying beep and it happens in some programs to and i cant get it to turn off.

---

### Post by joelwhrs on 2009-02-14
Please, does anybody know how to do this?? If nobody does how do i switch all my apps over to another username and just use that because it works on the other user. Please

---

### Post by neu2buntu on 2009-02-14
in reference to your post #2 , have you tried right click on speaker icon > preferences > and in the "select device and track to control" section have you chosen "master" here not "capture"

---

### Post by neu2buntu on 2009-02-14
and to post num #3 goto > preferences > sound > sounds ... and untick play alert sound should do it i hope

---

### Post by joelwhrs on 2009-02-14
I have my control set to master, i think when it stoped working i was playing around with the shortcut controls.

---

### Post by joelwhrs on 2009-02-14
When I disable the alert sound it goes to custom sounds and it seems to disable all the other sounds to:((

---

### Post by neu2buntu on 2009-02-14
try goto the shortcuts again and click on the volume up option until it lights up then hit corrosponding key and the same for the volume down ,if you havnt tried this already

---

### Post by joelwhrs on 2009-02-14
I've tried that pretty often already so i went in my brothers acount and his controls worked great.

---

### Post by neu2buntu on 2009-02-14
as for post #8 make sure you untick the 3rd button down "play alert sound" and not the 1st button "play alerts and sound effects" as this disables the login etc sounds

---

### Post by joelwhrs on 2009-02-14
Ok tried that and it works, Thanks alot now all i need to know is how to get my voume control shortcuts to work, but thanks alot.

---

### Post by neu2buntu on 2009-02-14
think i might have it . in my case the speaker icon shows master as my control device but in > preferences sound > devices it is set as pcm...   firstly try
[1] change your devive to control in the above mentioned window and try to see if it works

failing that goto your brother account and open up >prerferences > keyboard shortcuts .and copy (write down) the exact values for volume up and volume down then go back to your account and edit them to be the same ... here a screenshot of my values below



also in step [1] probably choose master here...ok

---

### Post by joelwhrs on 2009-02-14
I have checked and i have the same exact configuration as you do but i will copy my brothers and let you know what i find out

---

### Post by neu2buntu on 2009-02-14
did you also try step [1] and set value to master

---

### Post by joelwhrs on 2009-02-14
Ok i checked and we both have the same shortcuts, i was wondering if maybe something got changed in the configuration files that it controls the capture instead of master

---

### Post by joelwhrs on 2009-02-14
yeah the only thing that is there is master, no pcm or anything

---

### Post by neu2buntu on 2009-02-14
you read my mind am just looking at gconf now......  ok goto terminal type
```
gconf-editor
``` hit return. then pu;ll ddown "apps" and goto > gnome_settings_daemon .. pull it down and click on keybindings and check your volume settings here

---

### Post by neu2buntu on 2009-02-14
one more thing are you controlling the actual right device?  open "volume control" again and at the top of this window there is a pull down list of devices. make sure you have chosen something like "alsa mixer" here and not "capture" oh and also check this is what it is set to in > preferences > sound > device

---

### Post by joelwhrs on 2009-02-14
I checked and its what its supposed to be

---

### Post by joelwhrs on 2009-02-14
I checked and it says i got hdaintel(alsamixer)

---

### Post by joelwhrs on 2009-02-14
Here's a screenshot of my sound preferences

---

### Post by neu2buntu on 2009-02-14
i think theres your problem all along goto my post #19 your device is set to capture as in your screenshot (just above your highlighted "master") you need to chang this to "alsa mixer" here and also in volume control (speaker icon on top panel) fingers crossed this will solve it

---

### Post by joelwhrs on 2009-02-14
WOW it works thanks a million:)

---

### Post by neu2buntu on 2009-02-14
no problem... i should have thought of this before all the other posts but you learn everyday...good luck and here a great post by markbuntu that has got my sound setup just the way i want it so it may be usefull to you later
[http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack](http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack)

---

