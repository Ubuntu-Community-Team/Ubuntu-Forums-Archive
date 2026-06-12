---
title: "Can't select Blue Yeti Pro USB Microphone in sound settings menu"
date: 2013-06-10
forum: Multimedia Software
---

### Post by tomsa on 2013-06-10
Today, I recieved a shiny new Blue Yeti Pro USB microphone in the mail.  I did my research to make sure that it would work.  I found the following websites, and this is what led me to believe that it would work without any issues, despite the fact that it is a USB 2.0 device:
[http://community.linuxmint.com/hardware/view/12511]("http://community.linuxmint.com/hardware/view/12511")
[http://geardiary.com/2011/06/28/review-blue-microphone-yeti-pro/]("http://geardiary.com/2011/06/28/review-blue-microphone-yeti-pro/")
So- I got it out and plugged it in.  The red light on the mute button lit up and started flashing, which means that the Mic is muted.  I un-muted it- so far, so good.  I went to the sound settings menu.  It was recognized as: Digital Input (S/PDIF)  BLUE USB Audio 2.0 and BLUE USB Audio 2.0 Analog Stereo.  I tried to select them, one at a time as the input device.  Each time I tried to select it, the sytem settings would crash and shut off.  
    
    Then, I tried to select it using JACK instead.  In Jack, I was able to select it as the input device without issue.  I fired up the JACK server and didn't get loads of xruns, so I opened Ardour.  I couldn't get signal flowing in to Ardour no matter what I tried.  Now It's getting frustrating.  I shut off the JACK server and decided to try something else.  So next I open a terminal and fire up ```
alsamixer
``` and got similar results, the microphone is recognized and I selected it as the sound capture device. The levels look good so I open Audacity and select the microphone as the capture device in Audacity.  The same thing happened- no audio signal was getting in to the computer.  

    So, I decided to try installing and running ```
pavucontrol
```.  The microphone is recognized.  Great.  I can select it.  Great.  I fire up audacity again and the same thing happens- no audio signal to the computer.  The next thing I tried was killing pulse and just using ALSA.   I tried both ```
pactl exit
``` and ```
pulseaduio --kill
``` and try selecting the microphone again with alsamixer- same result each time, no signal to the computer.  

    At this point, I'm really frustrated.  I tried making sure of the the dumb stuff, like "is it plugged in"  and "maybe I should try the other USB ports".  No dice.  I tried the direct headphone monitor on the mic to see if it's picking up sound at all, and it is.  I'm completely baffled.  when I run ```
lsusb
``` in a terminal I get the following output: 
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 13d3:5710 IMC Networks 
Bus 002 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 006: ID 074d:0002 Micronas GmbH
```

I uplugged it and ran ```
lsusb
``` one more time to see which device it was for sure.  It's the Micronas GmbH device.  At least that's some information.  Then I ran ```
cat /proc/asound/cards
``` and got the following output:
```
0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdfc00000 irq 52
 1 [B20            ]: USB-Audio - BLUE USB Audio 2.0
                      BLUE BLUE USB Audio 2.0 at usb-0000:00:1d.0-1.2, high speed

```

    So- that's what I've got.  A pretty sweet microphone that would be a really useful tool if it worked.  I thought it would, and it doesn't.  I am completely perplexed and don't know what I should do next.  Does anyone have any ideas or advice?

---

### Post by tomsa on 2013-06-11
Here's some more information, though I don't know how useful it is.  When I open the System Settings from the Terminal with gnome-control-center I get the following output with regard to audio:
```
(gnome-control-center:3593): sound-cc-panel-WARNING **: active_output_update - couldn't find a stream from the supposed active output

(gnome-control-center:3593): sound-cc-panel-WARNING **: active_input_update - couldn't find a stream from the supposed active input

```

When I try to select my microphone, the System Settings Window still closes and I get this in the terminal:
```
Segmentation fault
``` 

MAybe there's something useful there

---

### Post by tomsa on 2013-06-11
Also, the microphone appears to work fine with a 12.04.2 live DVD but not with a 13.04, Linux Mint 15 or Mint Debian edition live DVD- is there a way to roll back the driver to the previous version so I don't have to reinstall my whole OS??

---

### Post by tomsa on 2013-07-09
Since all of this started, I have done a fresh Ubuntu Studio 13.04 install.  I decided to try this microphone again last week as a USB microphone during a practice session.  Lo and behold, it worked!  I thought everything was cool and packed it up to be used again in a few days...

I set it up to record a rehearsal today.  I changed NOTHING about my setup/settings since using is the last time. Once again, I could not get any audio into Jack/Ardour.  I checked Pulseaudio mixer- the microphone shows up as it should, but isn't pulling in audio.  I checked Alsamixer as well, and got the same results. I tried the liveUSB for Ubuntu Studio 13.04 again to try the same Jack settings, and the microphone worked again!  Reboot in to my regular install, and again, nothing.  I have absolutely no idea why I can't get this thing to work.  This is completely perplexing.  Is there an error log or some such thing that I could access and share that might lend a hand as far as debugging this hardware goes?

---

### Post by kwatson512 on 2013-07-16
I'm having the exact same issue with Blue Yeti and Mint 15. Anyone have an idea to fix this?

---

### Post by netbot on 2013-12-07
I had a strange behavior with this mic in my Ubuntu 12.04, maybe it is related to your issue, I'm posting my workaround perhaps it may be helpful to someone.

When I first plugged this mic via USB to my Ubuntu machine, it worked right away without further intervention. After rebooting the computer with the Blue Yet Pro plugged, it stopped capturing sound and the Mute light started to tick. After hours of frustration and investigation, I think the cause is the store procedure in the alsactl is saving the wrong parameters for this mic... I just opened the alsa file and deleted all the BLUE entries from the end of the file:

**sudo vim /var/lib/alsa/asound.state**

This needs to be deleted:

```

state.B20 {
    control.1 {
        iface MIXER
        name 'BLUE Clock Selector Playback Switch'
        value.0 true
        value.1 true
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.2 {
        iface MIXER
        name 'BLUE Clock Selector Playback Switch'
        index 1
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'BLUE Clock Selector Playback Volume'
        value.0 127
        value.1 127
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 127'
            dbmin -12700
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.4 {
        iface MIXER
        name 'BLUE Clock Selector Playback Volume'
        index 1
        value 107
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 127'
            dbmin -12700
            dbmax 0
            dbvalue.0 -2000
        }
    }
    control.5 {
        iface MIXER
        name 'BLUE Clock Selector Capture Switch'
        value.0 false
        value.1 false
        comment {
            access 'read write'
            type BOOLEAN
            count 2
        }
    }
    control.6 {
        iface MIXER
        name 'BLUE Clock Selector Capture Switch'
        index 1
        value false
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.7 {
        iface MIXER
        name 'BLUE Clock Selector Capture Volume'
        value.0 127
        value.1 127
        comment {
            access 'read write'
            type INTEGER
            count 2
            range '0 - 127'
            dbmin -12700
            dbmax 0
            dbvalue.0 0
            dbvalue.1 0
        }
    }
    control.8 {
        iface MIXER
        name 'BLUE Clock Selector Capture Volume'
        index 1
        value 127
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 127'
            dbmin -12700
            dbmax 0
            dbvalue.0 0
        }
    }
}
 
```

After deleting all the BLUE config settings from this file, just save the file and plug the USB cable in the Blue Yeti Pro or if it was already plugged, you will need to unplug it first and then re-plug it. Now, the red light should stay on and hopefully the mic should be working fine again. I tested with Audacity, Skype, ... and it produces an awesome crisp clear sound. I was able to reproduce the same problem and workaround in three different Ubuntu 12.04 computers.

I ended up having this mic disconnected when the computer boots up or shuts down, as it seems that this file gets modified at BOTH stages. I just plug it when I need it and my Ubuntu is up'n running, then when I don't need it anymore I disconnect it. I finished up buying a USB hub with a ON/OFF Switch button for this purpose... this way I can accomplish the same thing but just by pressing a button. If anyone is interested, the model I bought from Amazon was:

[http://www.amazon.de/gp/product/B00884N1XS/ref=oh_details_o01_s00_i00?ie=UTF8&psc=1](http://www.amazon.de/gp/product/B00884N1XS/ref=oh_details_o01_s00_i00?ie=UTF8&psc=1)


[B]_Note:_
[/B]
If you want to emulate the shutdown or booting up behavior, you just have to execute the following code having the Blue Yeti Pro connected:

**sudo alsactl store**

Now if you edit your asound.state file, you should see the BLUE config again, and if you try to switch off and on the mic, it won't work again.

Hope this helps.

---

### Post by MeditatingHamster on 2014-03-06
Thanks for that NetBot! You saved me a massive headache, had the same issue in 13.10 and removing the blue entries from **/var/lib/alsa/asound.state** you mentioned worked perfectly :-).

---

### Post by netbot on 2014-03-07
I'm glad I could help! :)

---

### Post by justin-embeddedmicro on 2014-04-16
I automated the workaround for anyone with a Yeti Pro.

First I created a Ruby scrip that will remove the offending section of the asound.state file. I named this file **blue_yeti_pro.rb** and put it in ~/Documents/Scripts/

```
#!/usr/bin/ruby

require 'fileutils'


File.open('/var/lib/alsa/asound.state.replace', 'w') do |f2|
    blue_yeti = false
    File.open('/var/lib/alsa/asound.state', 'r') do |f1|  
        while line = f1.gets  
            if blue_yeti
                if line == "}\n"
                    blue_yeti = false
                end
            else
                if line == "state.B20 {\n"
                    blue_yeti = true
                    next 
                end
                f2.write line
            end
        end  
    end  
end


FileUtils.mv('/var/lib/alsa/asound.state.replace', '/var/lib/alsa/asound.state')
```

Then I edited the file /lib/udev/rules.d/90-alsa-restore.rules by adding the line
```
TEST=="/var/lib/alsa/asound.state", RUN+="/usr/bin/ruby /home/justin/Documents/Scripts/blue_yeti_pro.rb"
```
right after 
```
LABEL="alsa_restore_go"
```
to cause the script to run before alsa tries to restore it's settings. Note that you'll need to update the path to the script on your computer.

The full file is as follows.
```
ACTION=="add", SUBSYSTEM=="sound", KERNEL=="controlC*", KERNELS!="card*", GOTO="alsa_restore_go"GOTO="alsa_restore_end"


LABEL="alsa_restore_go"
TEST=="/var/lib/alsa/asound.state", RUN+="/usr/bin/ruby /home/justin/Documents/Scripts/blue_yeti_pro.rb"
TEST!="/var/lib/alsa/state-daemon.conf", RUN+="/usr/sbin/alsactl -E HOME=/var/run/alsa restore $attr{device/number}"
TEST=="/var/lib/alsa/state-daemon.conf", RUN+="/usr/sbin/alsactl -E HOME=/var/run/alsa nrestore $attr{device/number}"


LABEL="alsa_restore_end"

```

The only problem I'm having with this workaround is that you have to select the Blue Yeti Pro from your settings every time you boot. However, it seems to work fine after being selected.

This is a bad solution, hopefully someone with more knowledge than I can fix the real bug.

I hope this helps some fellow Yeti owners out.

Justin

---

### Post by tomsa on 2014-07-02
Since posting this question I have found a solution! 

When Using JACK and Bitwig studio on 14.04, I was still getting the same behavior. It worked the first time, but was automatically muted for capture on subsequent reboots.  I am able to unmute the capture card using QasHctl now, where I was not able to do so in the Ubuntu Sound Settings Menu or Alsamixer.  

That's it.  Just unmute the Yeti Pro Capture card in QasHctl.  Problem Solved!

---

