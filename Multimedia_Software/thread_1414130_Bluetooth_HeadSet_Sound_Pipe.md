---
title: "Bluetooth HeadSet Sound Pipe"
date: 2010-02-23
forum: Multimedia Software
---

### Post by carthmen on 2010-02-23
Hello,

  I have got my headset connecting to the system using the BlueMan interface.  When I first did this it gave me a error about not being able to put the sound on-top of 'pulseaudio'.

  Well this well about the last straw between me and Mr. 'PulseAudio', so away he went.  I removed the demon via this instruction. [[ubuntu] Safely Remove Pulseaudio? - Ubuntu Forums]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273"). 

  I then tried connecting to my bluetooth headset again, no errors.  But the bluetooth  sound device does not show up in any mixer, or application.

  What else do i need to do to get this working again.  I know my hardware is fine, it used to work in the previous version of Ubuntu and it all works on my wifes Windoze XP computer.

---

### Post by carthmen on 2010-02-23
UPDATE:  I set this in the .asoundrc file in my home directory

pcm.bluetooth {
    type bluetooth
        device "00:19:7F:4B:37:65"
        profile "auto"         
}


Unfortuantly, this has not fixed the problem.  Still the bluetooth does not show up in any drop boxes.

---

### Post by carthmen on 2010-02-24
hmmm....I will try reposting in a different area perhaps...

---

