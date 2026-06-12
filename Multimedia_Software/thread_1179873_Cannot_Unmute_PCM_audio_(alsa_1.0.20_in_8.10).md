---
title: "Cannot Unmute PCM audio (alsa 1.0.20 in 8.10)"
date: 2009-06-06
forum: Multimedia Software
---

### Post by geekyhawkes on 2009-06-06
Hi;

I have just completed a fresh install of Kubuntu 810 and upgraded my ALSA to 1.0.20.  The problem I have is that I am getting no sound over HDMI within a KDE session.  I am not able to unmute the PCM channel.  When i select shutdown computer i get audio as KDE closes.

I have tried using aplay testsound.wav and still get no output, and have ran the aslamixer from within a terminal. Strangely, when run from terminal the PCM channel doesnt have a mute icon next to it (same in the gui). 

I have also tried ;

# amixer set Master 90% unmute
 # amixer set PCM 85% unmute

With no change sadly.

ANY help well recieved as this is driving me crazy!

---

### Post by geekyhawkes on 2009-06-06
Moving no where but have noticed the following:

In my bios i set the HDMI audio off, restarted the machine, KDE correctly detected the lack of HDMI audio card.  Shut down the machine and then re-activated HDMI audio in bios.  Started machine up KDE correctly found the HDMI audio device but still i could not unmute the audio.  

I checked my user name is against audio:x29 and it is.  

Following a log off and log back on I now get the first half of the log on sound from within KDE before the sound cuts out and again I cannot unmute the PCM.  

This is driving me crazy, every ALSA topic i find via google doesnt cover this, and I am really confused as to why KDE would mute the source during start and then not let me unmute it.  I am also confused as to why the source would be unmuted and play the shutdown sound (apart from to mock me!)


EDIT:  My issue sounds the same as here:  [http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=printview&t=8937&start=0](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=printview&t=8937&start=0)

Is there a way i can get around Kmix loading in kde?  Or find the profile it is loading that selects pcm at mute and delete/edit it?


I have followed all of the guides I can find here, but am still getting no where!  Its annyoing as sound is working for login and shutdown (well most of the sound file is played before the source is muted).  


I have tried to find the exact codec lines to add to alsa-base but my chipset isnt listed in any of the modelname lists i can find, i am running a Realtek ALC 1200 chipset and the highest i have found is the 880 stack.



As more detail the sound seems to work for the first few seconds (and last seconds) of each X session.  If i switch user then no sound is played at logon/log off but if i log off or Ctrl ALT Backspace then log in sound is fine (for a few seconds).



Not sure if i am getting anywhere or not (and updating this so someones search in the future is useful);

if i run aplay -Dplughw:0,3 test.wav then i get the sound file playing!  (o,3 is the HDMI found out from aplay -l).  I just need to find a way to direct all audio this route now.




I now have audio in amarok!

I Created an /etc/asound.conf file as follows:


pcm.!default {

        type hw
        card 0
        device 3

}


Seems to be a solution!




I have just found this entry over at an nvidia forum which is a fair bit more elegant;

Here's my asound.conf, found from finnish vdr forum [http://www.netholic.com/viewtopic.php?t=3050](http://www.netholic.com/viewtopic.php?t=3050) (thanks Rofa)

Code:

# cat /etc/asound.conf
# Aforin konffi
# [http://www.netholic.com/viewtopic.php?t=3050](http://www.netholic.com/viewtopic.php?t=3050)

pcm.!default {
        type plug
        slave {
                pcm multi
                rate 48000
        }
        ttable.0.0 1.0
        ttable.1.1 1.0
        ttable.0.2 1.0
        ttable.1.3 1.0
}

#ctl.!default hdmiout

pcm.optical {
        type hw
        card 0
        device 1
}

ctl.optical {
        type hw
        card 0
        device 1
}

pcm.hdmiout {
        type hw
        card 0
        device 3
}

ctl.hdmiout {
        type hw
        card 0
        device 3
}

pcm.multi {
        type multi
        slaves.a.pcm "hdmiout"
        slaves.a.channels 2
        slaves.b.pcm "optical"
        slaves.b.channels 2

        bindings.0.slave a
        bindings.0.channel 0
        bindings.1.slave a
        bindings.1.channel 1

        bindings.2.slave b
        bindings.2.channel 0
        bindings.3.slave b
        bindings.3.channel 1
}

ctl.multi {
        type hw
        card 0
}






RESULT!

---

