---
title: "No audio via HDMI/DP 20.04 | no hdmi/dp option in setting -&gt; sound -&gt; output device"
date: 2021-03-20
forum: Multimedia Software
---

### Post by krzysztof.czeladko on 2021-03-20
In my system there is no **HDMI/DisplayPort** option in setting -> sound -> output -> output device

Hi guys, I fought and found workaround ( for me it's just a temporary solution ) but maybe someone got proper way to fix it

Hardware: HP elitedesk 800 G4 DM  ( [https://support.hp.com/us-en/product/hp-elitedesk-800-65w-g4-desktop-mini-pc/21353734/document/c06045012](https://support.hp.com/us-en/product/hp-elitedesk-800-65w-g4-desktop-mini-pc/21353734/document/c06045012) )
Audio chipset is integrated in motherboard ( lspci: 00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10) , module: snd_hda_intel , Codec: Conexant CX20632 )
VGA chipset is integrated in cpu ( lspci: 00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Desktop) , vga is integrated gpu in cpu i5-8500 ) 

System: fresh install ubuntu and after that: apt update && apt upgrade. there was no sound via hdmi/dp at any point of instalation and updates.

Physical outputs at back panel:
#1: DP display port ( integrated in motherboard )
#2: DP ( integrated in motherboard )
#3: HDMI ( not integrated but used a dedicated HP expansion HDMI port ) 

**No sound** via any HDMI or DP (display port) output , can't even chose it **hdmi/DP** option inside setting -> sound -> output -> output device
Video is all right, any port works perfect.

I've tried lots of things mostly uninstall ( purge ) and install -> reboot , reinstall -> reboot  packages: 
```
alsa
alsa-tool
pulseaudio
intel-media-va-driver-non-free
intel-microcode
and maybe some more probably not important
```

change configuration settings in /etc/pulse/default.pa -> reload modules and force reload with new config:
```
# config check lots of options 
#1 
options snd-hda-intel model=hp
#2
options snd-hda-intel model=hp-laptop
#3
options snd-hda-intel model=auto
# etc 

```

none of above steps help ( I'm not saying there are necessary or not necessary, but those steps didn't help me right away) 

**Workaround **that help for me
somehow i found a tool **hdajackretask **( part of alsa-utils package )
and chose my codec: **intel kabylake hdmi **
in options checked : **show unconnected pins** ( physically always got connected minimum 1 of the video output #1 or #2 dp or else #3 hdmi to TV )
then in **pin configuration** showed up **3 not connected pins** with id
for each pin i checked **override** and select from **not connected** to **HDMI/DisplayPort**

**Apply now** & success :D , got **hdmi/dp** option setting -> sound -> output device, sound works fine via each port #1,#2 ( dp port via adapter dp -> hdmi + cable hdmi<->hdmi ) and port #3 hdmi ( dedicated hp internal adapter mb->dhmi + cable hdmi<->hdmi )

do not forget **install boot override **to run script each time when you start the system 

before **hdajackretask **configuration override:
[[IMG]https://i.ibb.co/BtgYbcH/remmina-192-168-1-6-192-168-1-6-2021321-02447-002183.png[/IMG]]("https://ibb.co/BtgYbcH") 

after **hdajackretask **configuration override applied:
 [[IMG]https://i.ibb.co/2P7RN1Q/remmina-192-168-1-6-192-168-1-6-2021321-02616-021049.png[/IMG]]("https://ibb.co/2P7RN1Q")


I can provide more logs, but those 2 should say something

that's my **alsa-info** log
[http://alsa-project.org/db/?f=a25cc2f0bf3c22c45e5528e678504d127467bf21](http://alsa-project.org/db/?f=a25cc2f0bf3c22c45e5528e678504d127467bf21)

and **pa-info** log
[URL="https://pastebin.pl/view/b45a103d"]https://pastebin.pl/view/b45a103d

[/URL][HR][/HR][URL="https://pastebin.pl/view/b45a103d"]
[/URL]Help me find what it wrong or maybe it's all right, because there's no correct implementation/configuration in packages with this chipset

From my point of view there is something wrong that my system doesn't recognize that HDMI/DP cable is connected to one of the video output ( #1,#2 DP, #3 HDMI ), i need somehow setup proper intel vga or intel hd audio drivers that will recognize when and where cable is connected and make sound output visible and possible to switch to HDMI/DP port. I'm not sure which package or configuration is responsible for it. Before **hdajackretask **override configuration there was no sound on TV. If anyone got better solution please share it here. Maybe I'm missing something in configuration: one line, blacklist some module, use special model in configuration of alsa or something else I would be very glad for any help.

Got only some time in weekend for test your solutions if any shows.

---

### Post by extremolo on 2022-01-16
Hi,

just signed up to say thank you very much :) Was fighting with similar problems for the last 10h, none of my other solutions worked.
Using a HP EliteDesk 800 with Intel UHD 630. The only way to get sound out of it via HDMI was your workaround. Even tried Fedora and had the same problem there.

Thanks again for your detailed post and have a good day :) 

Greetings
Extremolo

---

