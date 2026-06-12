---
title: "Ubuntu 10.10 Gigabyte G31M-ES2L enable 5.1 audio"
date: 2011-01-14
forum: Multimedia Software
---

### Post by spacevoid on 2011-01-14
Hey all,
I am trying to get the 5.1 audio working on the gigabyte g31m-es2l mobo which has ALC883 audio chipset.Its onboard audio.

Its a fresh installation of ubuntu.I have set the sound properties as below.The speaker test only works for the front right and front left speakers.Rest other speakers are muted.

[IMG]http://i.imgur.com/bWUGn.png[/IMG]

Also tried editing the /etc/pulse/daemon.conf file with uncommenting the audio channels from 2 to 6 and rebooting.Still its not working.

Tried running the following command and again only the front right and left speakers light up.

[IMG]http://i.imgur.com/ey4n2.png[/IMG]

Am I missing something here ? Please help me out.

---

### Post by spacevoid on 2011-01-15
Phew !! Finally got it to work. [IMG]http://www.techenclave.com/images/smilies/happy19.gif[/IMG]

Here is the thing to do:
Open Terminal and type without quotes "gksudo gedit /etc/modprobe.d/alsa-base.conf"
Add a comment at the end of the text at the bottom without quotes "options snd-hda-intel model=clevo-m540r"
Save the file and reboot.
Then in Sound Properties > Hardware Tab > Settings for selected device[IMG]http://www.techenclave.com/images/smilies/tongu23e.gif[/IMG]rofile : ANALOG SURROUND 5.1 OUTPUT

Thats it. Now I have 5.1 audio in VLC too.

---

### Post by lidex on 2011-01-15
Good job. For reference, is all sound working correctly - headphones, line, mic?

---

### Post by spacevoid on 2011-01-15
Since yesterday I have been trying to work out and found many threads here but didnt get any positive answer.

I have to thank you lidex coz of the immense contribution you have made in this forum.I truly appreciate that. :)

Coming to the topic at hand ... The motherboard actually has 7.1 audio and to access all the channels one needs to connect the front audio connectors to the motherboard's internal connectors,which I havent.So I am not sure what audio/mic/ is running on those connectors.

Not to sound confusing let me explain a bit.
The motherboard has 3 audio jacks at the back.When in stereo setup they work as (blue = linein), (Green = lineout/front right+left speakers) and (red = mic in). The default ubuntu install sets the system up as Stereo so the above config works.Even the mic works.But to make it work the audio profile needs to be setup as stereo duplex and then select input as mic.

After editing the alsa-base.conf file, the jacks now work as (blue = rear right+left) , (green =front right+left) and (red =center+sub).I have analog speakers Logitech X540. So I am getting the proper channel audio on the jacks which I wanted.

Now I am not sure what the front audio connectors carry as I havent connected them.So in short if I want to use the mic then I will have to re-edit the alsa-base file, reboot and get the mic to work.I know its tedious but I dont use the mic so it works out for me.

If in the future i get the front panel connectors then I ll check this out for sure. :)

---

### Post by lidex on 2011-01-15
Thanks for the feedback.I don't use a mic either, or headphones, so I forget to check if they are working as long as speakers do.
But you can't just change the profile (and possibly connector) in sound preferences to get the mic up?

---

### Post by spacevoid on 2011-01-15
Nope in the sound preferences I tried all the combinations listed but the mic doesnt come on. It has to be via the alsa-base.conf way.

---

### Post by freesoul.rahul on 2011-01-27
hey plz help me .. 

i dnt get the 5.1 option in my system->preference->audio->hardware dropdown list ...


i attached d attachment of the list .. it shows 4.0 dats it.
how did you manage to get "Analog Surround 5.1 Output" ???

---

### Post by lidex on 2011-01-27
> **freesoul.rahul said:**
> hey plz help me .. 

i dnt get the 5.1 option in my system->preference->audio->hardware dropdown list ...


i attached d attachment of the list .. it shows 4.0 dats it.
how did you manage to get "Analog Surround 5.1 Output" ???

See post #2

---

### Post by freesoul.rahul on 2011-01-28
this is what all i did

I edited the /etc/pulse/daemon.conf file and changed the audio channels from 2 to 6 and restart.
then
in terminal "gksudo gedit /etc/modprobe.d/alsa-base.conf"
add a comment at the end of the text at the bottom of file "options snd-hda-intel model=clevo-m540r"
save and reboot

even then
Then in Sound Properties > Hardware Tab > Settings for selected device
it doesnt show 5.1 option .. :(:( !!!

HELP PLzz
whot did i do wrong ????

---

### Post by spacevoid on 2011-02-04
Rahul... restore the  /etc/pulse/daemon.conf file to as it was earlier.Its not required.

Whats your motherboard make model ?

---

### Post by Bogdan_80 on 2011-02-04
Hello,

I have a Asus M2N motherboard with ADI1988 onboard sound card. What should I write at the model?

I had also edited daemon.conf like Rahul did, should I restore it? Now the sound works like 2.1 (rear speakers and subwoofer works, front speakers and center are dead)
I had also checked in alsamixer the volume for all devices to be maximum and unmute.

Thanks in advance

---

### Post by lidex on 2011-02-09
> **Bogdan_80 said:**
> Hello,

I have a Asus M2N motherboard with ADI1988 onboard sound card. What should I write at the model?

I had also edited daemon.conf like Rahul did, should I restore it? Now the sound works like 2.1 (rear speakers and subwoofer works, front speakers and center are dead)
I had also checked in alsamixer the volume for all devices to be maximum and unmute.

Thanks in advance

Try '6stack-dig' (for six analog outs) '3stack-dig' if only three

---

### Post by albyrock87 on 2011-03-11
> **spacevoid said:**
> "options snd-hda-intel model=clevo-m540r"

I tried, but it doesn't work.
Also I can't see the 5.1 option in the drop down list.

I have the same motherboard, can you attach your /etc/modprobe.d/alsa-base.conf ? thank you!

Edit 2:
Yey! Got it working with model=3stack-6ch
But i needed to update alsa driver, using this PPA:
[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

---

### Post by joaor10 on 2011-04-28
Thank you, you saved my day :D I have a G31M-ES2C and this worked like a charm.

Cheers!

---

### Post by iliopoulos on 2011-06-01
> **albyrock87 said:**
> I tried, but it doesn't work.
Also I can't see the 5.1 option in the drop down list.

I have the same motherboard, can you attach your /etc/modprobe.d/alsa-base.conf ? thank you!

Edit 2:
Yey! Got it working with model=3stack-6ch
But i needed to update alsa driver, using this PPA:
[https://launchpad.net/~ricotz/+archive/unstable]("https://launchpad.net/%7Ericotz/+archive/unstable")
  i have the same problem.. can anybody help me? i want exactly what to write in the terminal please. thank you!

---

### Post by lidex on 2011-06-04
> **iliopoulos said:**
> i have the same problem.. can anybody help me? i want exactly what to write in the terminal please. thank you!

Can't help you without knowing the hardware. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

