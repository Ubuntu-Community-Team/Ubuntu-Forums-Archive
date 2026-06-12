---
title: "Does Ekiga work?"
date: 2009-12-20
forum: Multimedia Software
---

### Post by batarce on 2009-12-20
I have added Ekiga. When I call [EMAIL="500@ekiga.net"]500@ekiga.net[/EMAIL] (echo test) there is no sound at all. After few minutes the webcan starts as I can see myself in the screen. It starts also a Call Duration time counting. But that is all, no sound, no record message, no echo... What should I do?

Marcelo

---

### Post by RedSingularity on 2009-12-22
Does your computer have sound at all?

---

### Post by batarce on 2009-12-26
Thanks for your reply. I thought I would never get a reply. 
Yes it has sounds because Skype works fine. In order to see if Ekiga would work I have changed the sounds set of my aspire one and now I dont know which sets it should be. But skype is still working. Can any one help me?

---

### Post by RedSingularity on 2009-12-26
What do you mean by "sound set"?

---

### Post by batarce on 2009-12-26
I meant to say that I went in Preferences>Sound>Devices and I changed the sets there. 

Now I have

Sound Events>Sound playback Autodetect

Music and Movies>Sound playback Autodetect

Audio Conferencing> Sound playback Auto detect and Sound Capture ALSA - Advanced Linux Sound Architecture

Defaul Mixer Tracks>Device HDA Intel (Alsa mixer)

---

### Post by RedSingularity on 2009-12-26
Thats fine.....mine is on autodetect as well.  As long as you have sound in other applications, like skype in your case, you don't need to play with those sound settings.  If you are having a sound problem in ekiga then it is a problem in that software alone.  In ekiga can you select pulseaudio in the sound preferences?

---

### Post by RedSingularity on 2009-12-26
I just opened ekiga and it looks like the sound preferences are located in Edit>Preferences.  Have you tried messing with the settings there?

---

### Post by batarce on 2009-12-26
I have tried some different sets for Audio Devices. It did not work. Now it is Default (PTLIB/ALSA). I have not however changed anything in Codecs.

---

### Post by RedSingularity on 2009-12-26
In a terminal try the following. 

gksudo gedit /etc/asound.conf

then add the following lines to the file.....

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

---

### Post by RedSingularity on 2009-12-26
In a terminal try starting ekiga this way.............

padsp ekiga

Then see if you have sound.

---

### Post by batarce on 2009-12-26
"then add the following lines to the file....."

Which file? Sorry I am newbie.

---

### Post by RedSingularity on 2009-12-26
When you run 

gksudo gedit /etc/asound.conf

it will open a blank file for you.  Add the lines to that blank file.

---

### Post by batarce on 2009-12-26
If you mean a new window, it did not open.

---

### Post by RedSingularity on 2009-12-26
Try running this before that gedit command

sudo touch /etc/asound.conf

---

### Post by batarce on 2009-12-26
now it opened I did not have typed a space after gedit... let me try now your lines

---

### Post by batarce on 2009-12-26
What should I do after type those lines in the file? Shoul I save?

---

### Post by batarce on 2009-12-26
I have not tried "sudo touch..." yet because the first one worked. I dont know what I do after typing those lines in the file

---

### Post by RedSingularity on 2009-12-26
Save it.

Then try opening ekiga like this in a terminal 


padsp ekiga

---

### Post by batarce on 2009-12-26
no sound still... I type [email]500@ekiga.net[/email] and press the green phone, my cam starts but there is no sound. Should I hear any sound?

---

### Post by RedSingularity on 2009-12-26
In ekiga Go to Edit>Preferences>Sound Events.  Try playing the different events.

---

### Post by batarce on 2009-12-26
Most of the events play.  Only the "sound for a new instant message" does not play it gives me the following message:

No incoming sound will be played.

The selected audio device was successfully opened but it is impossible to write data to this device. In case it is a pluggable device it may be sufficient to reconnect it. If not, or if it still is not accessible, please check your audio setup.

---

### Post by RedSingularity on 2009-12-26
Incoming sound doesnt play on mine either.  If it can play most sounds then your sound is working.  Can you have a friend call you or something to test it?  I would test it for you but i dont have an ekiga account.

---

### Post by batarce on 2009-12-26
i dont know anyone who have ekiga I am trying to install it to make my UBUNTU work with justvoip. If you have ekiga installed it is easy to have get an account LOL.

---

### Post by RedSingularity on 2009-12-26
Let me try setting up an account then. :)

---

### Post by RedSingularity on 2009-12-26
What number do i call you at?

---

### Post by batarce on 2009-12-26
is there any way to sending a private message in this forum? Then I give you my ekiga account

---

### Post by RedSingularity on 2009-12-26
Yeah click my name and it will say "send private message"

---

### Post by gradinaruvasile on 2009-12-26
Try Linphone. Maybe it will work. Its in the repositories.
Other stable SIP client that works fine is [[COLOR="Wheat"][COLOR="Gray"]_Sflphone_[/COLOR][/COLOR]]("http://www.sflphone.org/content/stable-release"). It does not have video support though.

Ekiga and SIP apps in general are prone to failure if the packages pass through firewalls/NAT. Its the SIP protocols fault mostly. It isnt designed to cope with internet pass-through - sometimes it works on and off, sometimes it does, sometimes doesnt work, and it varies depending the users environment (firewalls/routing/NAT etc), so there is no comprehensive guide for everyone. You see, the Skype protocol for example its designed with these issues in mind and it works reliably. SIP on the other hand tends to lose connections if there is a firewall that is not configured correctly or, sometimes the SIP packet passes through NAT(s) and the application just discards it, sometimes the application cannot handle the routing (Ekiga is my first example) when there are multiple active network interfaces/routes.

Some apps work more reliably than others though. 
I found that Linphone with all its simplicity is the most reliable and has the best sound quality. Havent tried it with webcam because for some reason i couldnt compile it with webcam support. 
Also Sflphone is a good one, i use it at work and from home through VPN and it works great.

Another thing to try is [[COLOR="Gray"]_Pidgin_[/COLOR]]("https://launchpad.net/~pidgin-developers/+archive/ppa") - the recent (Linux only) versions have audio/video support through Gtalk (essentially all Jabber based networks) that works quite reliably and its compatible with the Windows Gtalk (i tried audio only and it worked succesfully). See [[COLOR="Gray"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1348461") how to configure the audio/video plugin.

---

### Post by batarce on 2009-12-26
I did not find linphone at add/remove. Where should I look for it?

---

### Post by RedSingularity on 2009-12-26
Its in the Package manager.  Synaptic.

---

### Post by richardh on 2009-12-26
> **RedSingularity said:**
> Save it.

Then try opening ekiga like this in a terminal 


padsp ekiga

I have the same problem. Skype works.
In Eika, click on echo - I can see myself. Click on the sound button (a speaker like the Ubuntu sound icon) under the video and I get a popup which shows a dynamic sensor. When I speak, I can see sound is being picked up. No sound is coming back.

Tried calling another person with Ekiga. He could see me, hear me, but I could not hear him.

At bottom, there is a summary. I presume A:7.9/0.0 (a typical setting for this test), the outgoing sound is 7.9, but no incoming sound.

Just cant find a way to use Ekiga!!!!

---

### Post by gradinaruvasile on 2009-12-26
Ekiga from version 3.0 up doesnt work for me. If you have multiple interfaces, forget it. Try the other ones i suggested... for audio-video (open-source) Pidgin (the PPA version) should be the best bet... 
Also dont forget Skype - that thing is rock solid in Linux if you are not bothered by its proprietary code.

---

### Post by batarce on 2009-12-26
linphone did not work as well so far. I installed and when i start it opens a green windows. Is it normal?

---

### Post by gradinaruvasile on 2009-12-26
Try

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so linphone-3

in a terminal...

Also, check the multimedia settings (linphone -> preferences -> multimedia settings tab, video input device)

---

### Post by batarce on 2009-12-26
This line
LD_PRELOAD=/usr/lib/libv41/v411compat.so linphone-3

gave me
ERROR: ld.so: object '/usr/lib/libv41/v411compat.so' from LD_PRELOAD cannot be preloaded: ignored.
bash: linphone-3: command not found

---

### Post by gradinaruvasile on 2009-12-26
Then try this:

LD_PRELOAD=/usr/lib/libv4l/v4[COLOR="Red"]l1[/COLOR]compat.so linphone

copy-paste it, thats lowercase L, not 1. 
Also it seems that you have an older linphone version - 2.something. The 3.x binary is linphone-3, the 2.x is plain linphone.

What Ubuntu version u have?

---

### Post by batarce on 2009-12-26
do you mean preferences in linphone ? I did not find any multimedia setting tab there

---

### Post by batarce on 2009-12-26
it seems there is no green window anymore. but did not find multimedia tab settings

---

### Post by batarce on 2009-12-26
yes i have linphone 2.1.1. WHat is the best way to up it date

---

### Post by gradinaruvasile on 2009-12-26
> **batarce said:**
> it seems there is no green window anymore. but did not find multimedia tab settings

I based that post on the 3.2.1 versions menus. 
Does the webcam work ok?

Also, what Ubuntu version do you use?

---

### Post by batarce on 2009-12-26
i dont know how to find out what my Ubuntu version is. How do I do it?

---

### Post by gradinaruvasile on 2009-12-26
> **batarce said:**
> i dont know how to find out what my Ubuntu version is. How do I do it?
Click System -> About Ubuntu

---

### Post by batarce on 2009-12-26
sorry i did not find System

---

### Post by gradinaruvasile on 2009-12-26
> **batarce said:**
> sorry i did not find System

Hmmm.. U should have 3 menus on the top taskbar: Applications, Places, System.
Other method: open a terminal and type:

uname -r

press enter, copy-paste here the result.

Edit: on a second thought, the best way is

lsb_release -a

in a terminal.

---

### Post by batarce on 2009-12-26
2.6.28-17-generic

---

### Post by batarce on 2009-12-26
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

---

### Post by gradinaruvasile on 2009-12-26
Thats Jaunty - Ubuntu 9.04. 
There was a PPA that contained Linphone 3.0 but i couldnt find it. 
I compiled from source, made a .deb installer for the version 3.2.1 but it doesnt have the webcam module because it crashed the compilation so i had to remove it. I dont need it anyway.

just try your version - does it work?

---

### Post by batarce on 2009-12-26
I cant understand how it works... it did not ask for an account as normally this kind of software asks. I tried to set up my justvoip account but i could not.

---

### Post by gradinaruvasile on 2009-12-26
It doesnt ask. Post me a screenshot of the interface to guide you if i can. I have the newer version that is different.

---

### Post by gradinaruvasile on 2009-12-26
I found the latest (3.2.1) linphone in a PPA...

[https://launchpad.net/~domenico-martella-alcacoop/+archive/ppa/+packages](https://launchpad.net/~domenico-martella-alcacoop/+archive/ppa/+packages)

Add the ppa:
In a terminal:

sudo gedit /etc/apt/sources.list

paste the following line at the end of the file:

```
deb http://ppa.launchpad.net/domenico-martella-alcacoop/ppa/ubuntu jaunty main
```

Save, quit. Then type:

gpg --keyserver keyserver.ubuntu.com --recv C2D70F7E
gpg --export --armor C2D70F7E | sudo apt-key add -

Then:

sudo apt-get update && sudo apt-get dselect-upgrade

---

### Post by batarce on 2009-12-26
gpg --keyserver keyserver.ubuntu.com --recv C2D70F7E
gpg --export --armor C2D70F7E | sudo apt-key add -

Should I type it in the terminal?

---

### Post by gradinaruvasile on 2009-12-26
Yes. Those are 2 separate lines.

---

### Post by batarce on 2009-12-26
thanks ... it seems now i have the right version... but when i first started it pop up the message
Your machine appears to be connected to an IPv6 network. By default linphone always uses IPv4. Please update your configuration if you want to use IPv6

is it ok?

---

### Post by batarce on 2009-12-26
Now linphone is running. Could you please help me to set it up?

---

### Post by gradinaruvasile on 2009-12-26
Do you use ipv6? Thats the new internet protocol, not really used now - i heard that it is in use in Japan or something.
Should not be a problem.

The setup:
- Network settings:

First, if you use ekiga, set it to "behind nat/firewall ...", type
stun.ekiga.net as stun server

- Multimedia settings (next tab)

All to alsa:default device, check "Enable echo cancellation".
select your camera as video input device. If you see green, use the trick with the LD_PRELOAD (above).

- Manage SIP accounts

Ignore the default identity section. That is auto generated and its uses for direct pc-pc calls (sip:ipnumber type calls without server).

Click Add.

I attached a screenshot of my account setup (gradinaruvasile). Do exactly like it, just change my username to your username.

The rest of the settings are fine, no configuration needed.

---

### Post by batarce on 2009-12-26
I would not use ekiga. I would like to use justvoip [http://www.justvoip.com/en/index.html](http://www.justvoip.com/en/index.html) if it works.

in this justvoip webpage [http://www.justvoip.com/en/sipp.html](http://www.justvoip.com/en/sipp.html) I found it

**Software configuration**


                                                              **General**             
                                            [IMG]http://www.justvoip.com/images/dot2.gif[/IMG]             SIP port : 5060                                            [IMG]http://www.justvoip.com/images/dot.gif[/IMG]             Registrar : sip.justvoip.com                               [IMG]http://www.justvoip.com/images/dot2.gif[/IMG]             Proxy server : sip.justvoip.com                               [IMG]http://www.justvoip.com/images/dot.gif[/IMG]             Outbound proxy server : leave empty                               [IMG]http://www.justvoip.com/images/dot2.gif[/IMG]             Account name : your JustVoip username                               [IMG]http://www.justvoip.com/images/dot.gif[/IMG]             Password : your JustVoip password                               [IMG]http://www.justvoip.com/images/dot2.gif[/IMG]             Display name/number : your JustVoip username or voipnumber                               [IMG]http://www.justvoip.com/images/dot.gif[/IMG]             Stunserver (option) : stun.justvoip.com

---

### Post by gradinaruvasile on 2009-12-26
Ok. Then change the settings accordingly.

---

### Post by gradinaruvasile on 2009-12-26
Also, dont forget to set "My current identity" in the Linphone interface (lower left corner) to your sip account.

---

### Post by batarce on 2009-12-27
The software looks ok but I couldn't make it work with justvoip yet. The problem seems to be very similar to the one I had with Ekiga: no sounds. Is there any kind of echo test in linphone?

---

### Post by gradinaruvasile on 2009-12-27
Echo test is not in applications, its a server side service. 
Try without the stun server (set linphone to direct internet connection)

Ekiga servers have echo test enabled (500@ekiga.net). I suggest logging in an ekiga account and do the echo test.

---

### Post by gradinaruvasile on 2009-12-27
Have you used this service until now? If so, with what software/OS?

---

### Post by batarce on 2009-12-27
You can use it through the net. Like, you can log in and make a call which connects your phone to another phone. Or you can download a client software from their website and use it as well to make calls from your computer. They system are windows based I did not find for linux.

---

### Post by gradinaruvasile on 2009-12-27
I know the idea, i meant that did you use it succesfully?

---

### Post by batarce on 2009-12-27
Yes. I use both in windows and in the net.

---

### Post by batarce on 2009-12-27
I log in in my Ekiga account as you suggested and did echo test. For the first time I got "In call". But no sounds again.

---

### Post by batarce on 2009-12-27
does the sounds preferences in Ubuntu make any difference? What should they be?

---

### Post by batarce on 2009-12-27
I came back to Ekiga and now I got making calls. I think with more trying I will learn how linphone works as well. In Ekiga, playback is working ok but mic is not. I can hear but people can not hear to me. I found this out in the net 

[https://bugs.launchpad.net/alsa-driver/+bug/412106](https://bugs.launchpad.net/alsa-driver/+bug/412106) 

It seems there is in fact a problem with Ekiga's mic setup at least for aspire one.
In that same webpage there is a fix suggestion.

                 I found a fix for the issue. On Acer Aspire One A110 netbooks, the following seems to work:
 arecord -vv -f S16_LE -c2 -r8000 -d 5 test.wav; aplay test.wav
 But this didn't:
arecord -vv -f S16_LE -c1 -r8000 -d 5 test.wav; aplay test.wav
 On further investigation, it seems somehow having the Capture volume fields in alsamixer "linked" together is causing the issue. I unlinked them both by setting the left channel to 60% and the right channel to 0%. This fixed the above issue of recording with -c1.
 Ekiga also works just fine with this setting. I think this bug needs to be passed onto the alsa maintainer since it seems like wrong behavior that mic recording is affected by Capture's individual channel volume levels.

        

Unfortunately I am too newbie and I do not know how change the channels settings. Any help?

---

### Post by gradinaruvasile on 2009-12-27
Open a terminal, type:

alsamixer

press enter then press tab to get to the capture view. Make a screenshot (alt+printscreen) and post it here. I will tell you what to do next.

---

### Post by batarce on 2009-12-27
[IMG]file:///tmp/moz-screenshot-2.jpg[/IMG]I attached it because crtl C/crtl V did not work i dont know why.
[IMG]file:///tmp/moz-screenshot-4.jpg[/IMG][IMG]file:///tmp/moz-screenshot-5.jpg[/IMG]

---

### Post by gradinaruvasile on 2009-12-27
You are using Ubuntu 9.04 with PulseAudio. Thats not good. PulseAudio in 9.04 is crap. Only from 9.10 begins to work. I suggest use ALSA or upgrade to 9.10.

Anyways, press the up arrow to move the slider up.
If there is no change, read further.
Also, i would like to see the ALSA controls - those are the real sound controls, pulseaudio is a server on top of ALSA. That is done by going to system -> preferences -> sound and set everything to ALSA, then launch alsamixer again. And make a screenshot of the capture tab there.

---

### Post by batarce on 2009-12-27
Can you imagine that the problem is sorted out!?!? I mean, that was the problem maybe since the beginning. I could never imagine that it would have a happy end like that. It seems that the only problem was to move the slider up. THANK YOU to assist me on that.

How do I use Alsa instead PulseAudio as you suggested?

---

### Post by batarce on 2009-12-27
> **gradinaruvasile said:**
> You are using Ubuntu 9.04 with PulseAudio. Thats not good. PulseAudio in 9.04 is crap. Only from 9.10 begins to work. I suggest use ALSA or upgrade to 9.10.

Also, i would like to see the ALSA controls - those are the real sound controls, pulseaudio is a server on top of ALSA. That is done by going to system -> preferences -> sound and set everything to ALSA.

Is that what I should change?

---

### Post by gradinaruvasile on 2009-12-27
> **batarce said:**
> Can you imagine that the problem is sorted out!?!? I mean, that was the problem maybe since the beginning. I could never image that it would have a happy end like that. It seems that the only problem was to move the slider up. THANK YOU to assist me on that.

How do I use Alsa instead PulseAudio as you suggested?

Well im happy for you. Next time you should check the basics first... ;)

Well if the sound is working properly in all apps and the pulseaudio process doesnt eat  all your CPU from time to time, no need. But if you got problems (i did) there are a 2 options to get rid of pulseaudio:

First:remove completely pulseaudio
1. system->preferences->sound, set all to alsa
2.in a terminal:
sudo apt-get purge pulseaudio
reboot.
Thats it.

Second: disable pulseaudio:

1. system -> preferences -> sound, set all to alsa
2. in a terminal:

sudo apt-get install alsa-oss libasound2 libasound2-plugins sysv-rc-conf

sudo mv /etc/X11/Xsession.d/70pulseaudio ~/

3.i a terminal:

sudo gedit /etc/pulse/client.conf

Look for this line ‘autospawn = yes’ then change it to ‘autospawn = no’
4. in a terminal: 
sudo gedit /usr/share/alsa/alsa.conf

Comment out the line which says ‘/usr/share/alsa/pulse.conf‘ by inserting a # in the beginning. After the change, the @hooks section would look something like the following.

@hooks [
    {
        func load
        files [
#           "/usr/share/alsa/pulse.conf"
            "/usr/share/alsa/bluetooth.conf"
            "/etc/asound.conf"
            "~/.asoundrc"
        ]
        errors false
    }
]

6. system > preferences -> autostart applications (or sessions) and add a new autostart application
name: kill pulseaudio
command: killall pulseaudio

reboot.

---

### Post by gradinaruvasile on 2009-12-27
> **batarce said:**
> Is that what I should change?

Yes. All of them.

---

### Post by batarce on 2009-12-27
> **gradinaruvasile said:**
> You are using Ubuntu 9.04 with PulseAudio. Thats not good. PulseAudio in 9.04 is crap. Only from 9.10 begins to work. I suggest use ALSA or upgrade to 9.10.

Also, i would like to see the ALSA controls - those are the real sound controls, pulseaudio is a server on top of ALSA. That is done by going to system -> preferences -> sound and set everything to ALSA, then launch alsamixer again. And make a screenshot of the capture tab there.

I do it tomorrow.

---

