---
title: "About PipeWire and PulseAudio on Xubuntu 22.04"
date: 2022-05-09
forum: Multimedia Software
---

### Post by &amp;KyT$0P# on 2022-05-09
Given that Xubuntu 22.04 comes with Pipewire, I have been investigating replacing PulseAudio with PipeWire, because PipeWire reportedly has lower latency than PulseAudio.  Initial testing based loosely on [these instructions]("https://ubuntuhandbook.org/index.php/2022/04/pipewire-replace-pulseaudio-ubuntu-2204/") suggests that PipeWire might be the solution to some long-standing audio issues I've had in VMs.

So I'm leaning toward going for replacing PulseAudio with PipeWire, at least in VM.

But I'm running into a lot of confusion that makes me hesitate, much of which I think ultimately stems from these questions:

1) What do PipeWire and pipewire-media-session do in **Xubuntu** 22.04 **default** configuration?  As far as I can tell, all audio is being handled by PulseAudio.  The only references I was able to find to why PipeWire is included by default in any Ubuntu flavor is maybe something about GNOME screen sharing? :confused:

2) Is there any reason I shouldn't just purge pipewire-media-session no matter what?  If I want to use PipeWire, I would use wireplumber (which even the pipewire-media-session package description recommends!).  And if I want to continue using PulseAudio, then will uninstalling pipewire-media-session cause any issues, even if I don't also uninstall PipeWire itself?

3) Why do all the guides about replacing PulseAudio with PipeWire in Ubuntu give strong warnings not to do it on production systems?  I have not been able to find any concrete reasons behind these warnings that seem to apply to 22.04.

Thanks for any clarification.

---

### Post by #&amp;thj^% on 2022-05-09
The best I can say is "Dropin replacement for Pulse"

PipeWire also supports containers like Flatpak and does not rely on the audio and video user groups. Instead, it uses a Polkit-like security model, asking Flatpak or Wayland for permission to record screen or audio.

Current plan is to develop wireplumber and deprecate pipewire-media-session. If you don't have any problems with pipewire-media-session, no reasons to switch right now. 

If you want to rollback all the changes:
```
systemctl --user unmask pulseaudio
systemctl --user --now disable pipewire{,-pulse}.{socket,*********    
systemctl --user --now enable pulseaudio.service pulseaudio.socket
```

Note:that wireplumber can be an optional replacement for pipewire-media-session
Discussion on that: [https://forum.endeavouros.com/t/pipewire-pipewire-media-session-vs-wireplumber/20705](https://forum.endeavouros.com/t/pipewire-pipewire-media-session-vs-wireplumber/20705)
My daily driver isn't Ubuntu, but I've been on it for a while now, no complaints on my end, but your mileage may vary
```
wpctl status
PipeWire 'pipewire-0' [0.3.51, me@arch-me, cookie:<Sniped>]
 &#9492;&#9472; Clients:
        34. xfce4-pulseaudio-plugin             [0.3.51, me@arch-me, pid:1075]
        35. pipewire-pulse                      [0.3.51, me@arch-me, pid:1111]
        36. Blueman                             [0.3.51, me@arch-me, pid:730919]
        53. wpctl                               [0.3.51, me@arch-me, pid:742888]
        72. WirePlumber                         [0.3.51, me@arch-me, pid:730057]
        76. WirePlumber [export]                [0.3.51, me@arch-me, pid:730057]
        77. Strawberry device finder            [0.3.51, me@arch-me, pid:273032]
        78. strawberry                          [0.3.51, me@arch-me, pid:273032]
        84. xdg-desktop-portal                  [0.3.51, me@arch-me, pid:325652]
        85. Firefox                             [0.3.51, me@arch-me, pid:9]
        86. virt-manager                        [0.3.51, me@arch-me, pid:676762]
        92. virt-manager                        [0.3.51, me@arch-me, pid:676762]

Audio
 &#9500;&#9472; Devices:
 &#9474;      37. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;      38. UOEOS Laptop Dock                   [alsa]
 &#9474;      39. HDA NVidia                          [alsa]
 &#9474;      55. SRS-XB22                            [bluez5]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      31. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.74]
 &#9474;      60. UOEOS Laptop Dock Digital Stereo (IEC958) [vol: 0.74]
 &#9474;  *  100. SRS-XB22                            [vol: 0.70]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;      58. UOEOS Laptop Dock Digital Stereo (IEC958) [vol: 0.74]
 &#9474;  *   62. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.74]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
       112. strawberry                                                  
            114. output_FL       > SRS-XB22:playback_FL
            123. output_FR       > SRS-XB22:playback_FR

Video
 &#9500;&#9472; Devices:
 &#9474;      43. Integrated Camera                   [v4l2]
 &#9474;      44. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   33. Integrated Camera                  
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    bluez_output.F8_DF_15_7F_64_73.a2dp-sink
         1. Audio/Source  alsa_input.pci-0000_05_00.6.analog-stereo

```

---

### Post by &amp;KyT$0P# on 2022-05-09
Thanks for the reply 1fallen, that link explains why pipewire-media-session would be used instead of wireplumber.  Which maybe another indication that Xubuntu 22.04 stock PipeWire setup might be for some sort of screen sharing?

Good to know you find PipeWire stable.
Your PipeWire version seems to be newer than here -
```
$ pipewire --version
pipewire
Compiled with libpipewire 0.3.48
Linked with libpipewire 0.3.48
```
Just curious, did you happen to be on PipeWire version 0.3.48 for a significant period of time?

---

### Post by #&amp;thj^% on 2022-05-09
> **halogen2 said:**
> Thanks for the reply 1fallen, that link explains why pipewire-media-session would be used instead of wireplumber.  
On the contrary they Highly recommend wireplumber.
> **halogen2 said:**
> 
Just curious, did you happen to be on PipeWire version 0.3.48 for a significant period of time?
About a month solid on wireplumber, I find  pipewire-media-session a bit stale now. :)
Don't get me wrong there is still a lot polish needed IE: wireplumber-cli
```
wpctl info
Usage:
  wpctl [OPTION&#8230;] COMMAND [COMMAND_OPTIONS] - WirePlumber Control CLI

Commands:
  status 
  inspect ID
  set-default ID
  set-volume ID VOL
  set-mute ID 1|0|toggle
  set-profile ID INDEX
  clear-default [ID]

Help Options:
  -h, --help       Show help options

Pass -h after a command to see command-specific options

```
 On impish 21.10 I was nice enough, installing and un-installing did not muck anything up.
EDIT: In fact It helped with my bluetooth problem.
clean install and clean un-install.

---

### Post by &amp;KyT$0P# on 2022-05-09
> **halogen2 said:**
> 2) Is there any reason I shouldn't just purge pipewire-media-session no matter what? ... And if I want to continue using PulseAudio, then will uninstalling pipewire-media-session cause any issues, even if I don't also uninstall PipeWire itself?

Although initial testing in disposable environment didn't show any difference, turns out this configuration does break some stuff, it's just very subtle.  Apparently, if PipeWire is running, and neither pipewire-media-session nor wireplumber are active, some apps will just hang starting even if PipeWire is not actually used.

> **1fallen said:**
> About a month solid on wireplumber,...
 On impish 21.10 I was nice enough, installing and un-installing did not muck anything up.
EDIT: In fact It helped with my bluetooth problem.
clean install and clean un-install.

Appreciate the input.  Based on your posts and my experience so far, seems PipeWire is pretty stable to use at this point, and that it wouldn't be as crazy as the warnings around the web indicate to consider replacing PulseAudio with PipeWire even on my main system.

---

### Post by #&amp;thj^% on 2022-05-10
> **halogen2 said:**
> Thanks for the reply 1fallen, that link explains why pipewire-media-session would be used instead of wireplumber.  Which maybe another indication that Xubuntu 22.04 stock PipeWire setup might be for some sort of screen sharing?

Good to know you find PipeWire stable.
Your PipeWire version seems to be newer than here -
```
$ pipewire --version
pipewire
Compiled with libpipewire 0.3.48
Linked with libpipewire 0.3.48
```
Just curious, did you happen to be on PipeWire version 0.3.48 for a significant period of time?

Sorry late reply, Ok I mention Pipewire && Wireplumber, I started pipewire at least a year ago now, very stable on arch, >>Ubuntu 20.04 needed some attention at a user level, kind of hit and miss as you now have seen in your "test bed", install is kind of cumbersome, so that might be where you hear about those warnings on "20.04" done incorrectly, will break all or most of the sound functions.
Apparently, they now want to replace Pipewire with Wireplumber, and I've been on that for a little over a month now.
I have no complaints, still wrapping my head around tho, looks promising in my view. (Mind Set of a Tester)
Kind of like ALSA on steroids. :)
Since this last post 5/10/20 I have received 3 wireplumber updates 5/11/22, still looks promising.

---

### Post by &amp;KyT$0P# on 2022-05-10
> **1fallen said:**
> Ubuntu 20.04 needed some attention at a user level, kind of hit and miss as you now have seen in your "test bed", install is kind of cumbersome, so that might be where you hear about those warnings on "20.04" done incorrectly, will break all or most of the sound functions.

This answers my question #3.  Thanks! :KS

---

### Post by &amp;KyT$0P# on 2022-05-12
Bump, because I still have no idea about this -
> **halogen2 said:**
> 1) What do PipeWire and pipewire-media-session do in **Xubuntu** 22.04 **default** configuration?


I'm now investigating using a more recent version of PipeWire than is in the standard Ubuntu repositories, and it might be important to check that whatever changes I make to PipeWire don't negatively impact the purpose of Xubuntu 22.04 default configuration of PipeWire.

---

### Post by #&amp;thj^% on 2022-05-12
Not here with Wireplumber:
```
Sound Server-1: ALSA v: k5.17.6-zen1-1-zen running: yes
  Sound Server-2: PipeWire v: 0.3.51 running: yes

```
before anyone gets confused, >> all this is still in planning (almost beta like) and needs to be implanted to our systems.
When all is settled it will be "Wireplumber"
EDIT: I guess I should include a minor bug as of a week ago>> Bluetooth wont start from a cold boot, I have to suspend the session and wake it for it to show.
with one bug on my end:
```
May 12 09:22:23 arch-me bluetoothd[2537]: src/profile.c:record_cb() Unable to get Hands-Free Voice >

```
All and all I see some good potential for Audio, now and in near future.

---

### Post by &amp;KyT$0P# on 2022-05-14
Thanks 1fallen for the heads up about Bluetooth on the latest version of PipeWire.  I don't have Bluetooth in the VM but will keep in mind if I switch to PipeWire+wireplumber for audio on my physical machines.

> **halogen2 said:**
> 1) What do PipeWire and pipewire-media-session do in **Xubuntu** 22.04 **default** configuration?

bump

---

### Post by #&amp;thj^% on 2022-05-14
> **halogen2 said:**
> 
bump

I guess a drop in replacement for pulseaudio was not good enough.

It aims to reduce bloat and bugs which pulseaudio&#8230;Well do i need to say anything more?
It blurs the line between normal / pro audio more, so it&#8217;s by default will accept much more use-cases for different users (a.k.a jack-like)
PipeWire was designed with a powerful security model that makes interacting with audio and video devices from containerized applications easy, with supporting Flatpak applications being the primary goal.

More from the man himself: [https://fedoramagazine.org/pipewire-the-new-audio-and-video-daemon-in-fedora-linux-34/](https://fedoramagazine.org/pipewire-the-new-audio-and-video-daemon-in-fedora-linux-34/)
That link is 1 year old now and a lot more has changed since.
```
systemctl --user status pipewire pipewire-session-manager pulseaudio
**_Unit pulseaudio.service could not be found._**
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; disabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-05-14 08:17:39 MDT; 1h 23min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 1059 (pipewire)
      Tasks: 2 (limit: 8741)
     Memory: 7.5M
        CPU: 64ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472; 1059 /usr/bin/pipewire

May 14 08:17:39 arch-me systemd[935]: Started PipeWire Multimedia Service.

&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-05-14 08:17:39 MDT; 1h 23min ago
   Main PID: 1060 (wireplumber)
      Tasks: 4 (limit: 8741)
     Memory: 29.4M
        CPU: 1.711s
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wireplumber.service
             &#9492;&#9472; 1060 /usr/bin/wireplumber

```
I guess I'm confused over how it will be used in Ubuntu then.
Many questions and answers :[https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/FAQ#is-pipewire-just-another-gstreamer](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/FAQ#is-pipewire-just-another-gstreamer)
It's the cats pajamas to coin a phrase. :)

---

### Post by &amp;KyT$0P# on 2022-05-14
It gets even more mysterious.  As those links also mention PipeWire video under Wayland and GNOME, I decided to test this theory -
> **halogen2 said:**
> The only references I was able to find to why PipeWire is included by default in any Ubuntu flavor is maybe something about GNOME screen sharing? :confused:

So I spun up a temporary Ubuntu 22.04 VM.  If I use the Wayland session, OBS does offer PipeWire screen capture options.  Although they just give blank screen, there are several indications the PipeWire side is actually working correctly (so I blame the blank screen on insufficient graphics capabilities of VM and assume this would work on real hardware).  If I switch to Xorg, OBS doesn't offer PipeWire capture anymore, and the existing added PipeWire capture can't be used or edited, the Properties window just says something like "No properties found".

I gather from this that PipeWire can't do screen capture/sharing under Xorg (at least in default Ubuntu configuration).  So its purpose in Xubuntu, which has no Wayland session, is likely not for screen capture/sharing either.

---

### Post by #&amp;thj^% on 2022-05-15
> **halogen2 said:**
>   As those links also mention PipeWire video under Wayland and GNOME, I decided to test this theory -


So I spun up a temporary Ubuntu 22.04 VM.  If I use the Wayland session, OBS does offer PipeWire screen capture options.  Although they just give blank screen, 
I gather from this that PipeWire can't do screen capture/sharing under Xorg (at least in default Ubuntu configuration).  So its purpose in Xubuntu, which has no Wayland session, is likely not for screen capture/sharing either.
Just pointing out that you need the packages xdg-desktop-portal-wlr and slurp, or you won't be able to see the screen capture option.

I would have to agree with you on VM or KVM, for now it runs best on bare metal.

Most applications used to rely on X11 for capturing the desktop (or individual applications), for example when using WebRTC in web browsers (e.g. on Google Hangouts). On Wayland, the sharing mechanism is handled differently for security reasons. PipeWire enables sharing content under Wayland with fine-grained access controls.

This requires xdg-desktop-portal and one of its backends to be installed. The available backends are:
[list]
    [*]xdg-desktop-portal-gnome for GNOME.
    [*]xdg-desktop-portal-kde for KDE.
    [*]xdg-desktop-portal-wlr for wlroots-based Wayland compositors (e.g. Sway, dwl)[/list]

Firefox (84+) supports this method by default, while on Chromium (73+) one needs to enable WebRTC PipeWire support by setting the corresponding (experimental) flag at the URL chrome://flags/#enable-webrtc-pipewire-capturer.

obs-studio (27+) supports this method by using the new PipeWire capture source. 

I know you may not be interested but slurp will help in wayland sessions:
```
slurp/jammy 1.3.2-1 amd64
  cli utility to select a region in a Wayland compositor

```
And a friendly reminder, It will take some time for many applications to move away from the Xorg API to the more general pipewire API.

To select shared monitor with xdg-desktop-portal-wlr if you have more than one, install slurp and add the following configuration (see xdg-desktop-portal-wlr(5) §&#8239;SCREENCAST OPTIONS):

```
~/.config/xdg-desktop-portal-wlr/config

chooser_type = simple
chooser_cmd = slurp -f %o -ro

```
When sharing a screen is requested, slurp will present you with a crosshair cursor and you'll need to click the screen you want to share. After the selection, xdg-desktop-portal-wlr will allow sharing that screen.

Audio
If Microphone is not detected by PipeWire

PipeWire's alsa-monitor module uses alsa-card-profiles to detect devices by default. If this is not working for you, try to turn off api.alsa.use-acp, or optionally turn on api.alsa.use-ucm. 

But I'm full wireplumber as of now so:
Otherwise, if using wireplumber: 
/etc/wireplumber/main.lua.d/50-alsa-config.lua (or ~/.config/wireplumber/main.lua.d/50-alsa-config.lua)
```
...
alsa_monitor.rules = {
    {
        ...
        apply_properties = {
            -- Use ALSA-Card-Profile devices. They use UCM or the profile
            -- configuration to configure the device and mixer settings.
            -- ["api.alsa.use-acp"] = true,
 
            -- Use UCM instead of profile when available. Can be
            -- disabled to skip trying to use the UCM profile.
            ["api.alsa.use-ucm"] = true,
...
```

Then, restart pipewire and check available devices:
For now, you have just about tapped my knowledge with all Pipewire and Wireplumber.
I figure this will be brought up more and more in the forums as time progresses.

---

### Post by &amp;KyT$0P# on 2022-05-15
> **1fallen said:**
> Just pointing out that you need the packages xdg-desktop-portal-wlr and slurp, or you won't be able to see the screen capture option.

Thanks for confirming that PipeWire screen capture/sharing is Wayland-only.  So that's definitely not why Xubuntu includes PipeWire by default.

At this point we've ruled out everything I was aware PipeWire does.  So I dug more deeply into the links 1fallen provided, to try to get a complete overview of PipeWire's capabilities.  And discovered that PipeWire has one purpose I didn't know about and hadn't played with yet: webcams.

That can be tested by installing the flatpak of Kamoso and disabling its direct access to devices (through Flatseal).  And indeed, then Kamoso displays the webcam when default configuration of PipeWire/pipewire-media-session is enabled, and only gives black screen if I disable/remove PipeWire!

So the answer to what PipeWire does by default in Xubuntu 22.04 is: It is used for webcam access, in some programs PipeWire provides better performance than other means of accessing the webcam.

Thank you again 1fallen for all your insights, I understand PipeWire much better now.  Looking forward to using it!

---

### Post by #&amp;thj^% on 2022-05-15
I'm looking forward to your results as it pulls in naturally not as I have done for testing only.
halogen2  I truly like your post's, you make me think** deeper than normal**, keeps it fun for me.
and I'm very sure some* frustration on your part, your a very nice addition to the forums.

---

### Post by &amp;KyT$0P# on 2022-05-26
On a related note, [https://discourse.ubuntu.com/t/pipewire-as-a-replacement-for-pulseaudio/28489/3](https://discourse.ubuntu.com/t/pipewire-as-a-replacement-for-pulseaudio/28489/3)

---

