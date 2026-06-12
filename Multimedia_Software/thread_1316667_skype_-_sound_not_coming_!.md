---
title: "skype - sound not coming ??!"
date: 2009-11-06
forum: Multimedia Software
---

### Post by chinmaya_n on 2009-11-06
hi

I've got a problem !
Though i can hear songs from my head phone, i could not here my friends voice in skype ! :(
My headphone speaker doesnt work, it has got some problem but i thought of hearing the voice from other side atleast but i could not... does anyone know ab't this!!?

Even i checked with sound preferences it didnt detect!! ( i mean if it detects it should play some blur sound in the speakers )
But i could listen to songs and happyly see movies !!

What is the problem?
can someone plz help me

---

### Post by cosine352 on 2009-11-06
these are my sound settings for the system and the skype and works fine. To get the microphone boost click on the preferences in the volume control menu and select the right switches (see pictures).

---

### Post by chinmaya_n on 2009-11-06
Mine are these........ !
Can u tell something?!!
I could not find it ! :(

---

### Post by cosine352 on 2009-11-06
just try different setting of the sound and see if that works. try with the settings I have.

---

### Post by chinmaya_n on 2009-11-06
I 've been trying since na hour and then posted it :)
I thought of having your settings but your sound system and mine look different.... i dont 've your prefrences in my system !! :(

The first thing i've to do is to get detected with sound preferences ( getting some blur sound when tested )....
Recently i've upgaded my ALSA's new version due to some sound problem.... does this caused any problem .......?

---

### Post by kostkon on 2009-11-06
What type of headphones do you have? USB?

---

### Post by chinmaya_n on 2009-11-07
Mine is not an usb one general one!

Just now i changed some settings in sound preferences..... Hurray :p It worked !!:popcorn:
You can see it in the picture! 

Thanxx everyone!

---

### Post by zatix on 2009-11-07
I am having the same problem but my sound prefernces are quite different, do you have ubuntu 9.10 and gnome?

here you have a screenshot[ 	  ]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8262588")

---

### Post by chinmaya_n on 2009-11-09
It shows mute in the picture... just check it out!

Its all right then, can you here songs or any multimedia through your headset !
If so keep the headset to the computer and restart, It worked for me that way!

---

### Post by chinmaya_n on 2009-11-09
my headphone worked not only b'se of the settings , i also restarted the system ,headphones being connected to it. usually i plug headphone just when needed.
If this is the case i've to restart the system when ever i 've to use the SKYPE.....!!
What should i do?

Can we restart the sound system and sound ports so that the skype detects it through a command ?

---

### Post by Arisha on 2009-11-09
maybe something with colomn:popcorn:

---

### Post by brianfactors on 2009-11-09
The problem, as I understand it, is with PulseAudio and Skype not getting along. Skype tends to hog the sound system, not letting anything else past and not wanting to share.

In Janty, the solution for me was just to remove pulse. It's the package "pulseaudio" which you can remove from Synaptic or from the command line.

In my case, an upgrade to Karmic took all my worries away. Yay! It works. And it works really well, too. So I'd recommend you update, and then get back to us.

PS: Installing Skype from Medibuntu might be a much better option than downloading the package from their site. [http://www.medibuntu.org/](http://www.medibuntu.org/) When I upgraded, I had to re-install Skype to get it to work.

---

### Post by chinmaya_n on 2009-11-10
My system is fully upgraded from jaunty to karmic!
And i've recently reinstalled the ALSA to new version manually due to some problems with audio!
Rightnow i'm downloading skype from medibuntu, i'll tel the result in my next post!

Edit: Mine is 1.0.21 (**$cat /proc/asound/version**)
and your might be 1.0.19 !

---

### Post by chinmaya_n on 2009-11-10
I installed skype-static from medibuntu.com .......... but it didnt work!
I've to do the previous way!

---

