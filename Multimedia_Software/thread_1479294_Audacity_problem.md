---
title: "Audacity problem"
date: 2010-05-10
forum: Multimedia Software
---

### Post by Jammanuser on 2010-05-10
Hello,
I am trying to record in Audacity in Ubuntu 8.10 64 bit on a Dell Studio 1535 laptop.
The problem is not that its not recording, per se.
Rather, the problem is its not recording the way that I want it to. :)

Its recording from the built-in mic, and I want to use the mic jack instead as a line in from a guitar (well, technically, an acoustic-electric resonator, but its close enough to a guitar to call it a guitar). 

I have tried using various devices for recording, and changing settings in both the Volume Control and Sound Preferences, but no matter what I do, Audacity still records from my built-in microphones, instead of from the line-in.

Please help.

Thanks in advance.

-Jam Man
:guitar:

---

### Post by Jammanuser on 2010-05-10
Funny thing is I remember recording using the mic jack alone before, but unfortunately I cannot remember what I did to achieve this affect. :(

---

### Post by cchhrriiss121212 on 2010-05-10
Edit>Preferences>Audio I/O, and you should be able to switch to the line in under "Recording".

---

### Post by Jammanuser on 2010-05-10
> **cchhrriiss121212 said:**
> Edit>Preferences>Audio I/O, and you should be able to switch to the line in under "Recording".
Yes, I tried that already.
Under "Recording", it shows two devices:

> OSS /dev/dsp
ALSA: HDA Intel: STAC92xx Analog (hw:0,0)
and I've tried selecting both already, but nothing changes. Having it set to either one will still record from the built-in mic, instead of line-in.

Any other ideas?

Thanks for the reply.

---

### Post by cchhrriiss121212 on 2010-05-11
You might want to check preferences>sound to see which device is default for recording. You could also switch to jackd, which will give you complete control over sound routing.

---

### Post by Jammanuser on 2010-05-11
> **cchhrriiss121212 said:**
> You might want to check preferences>sound to see which device is default for recording. You could also switch to jackd, which will give you complete control over sound routing.
Yes, I checked that already too, and it was originally set to "OSS - Open Sound System". I've tried setting it to different options, but no matter what I do, it still records from the mic, instead of the mic jack.

I guess I'll try jackd then. Is that a CLI or GUI program?

EDIT: Nevermind. Its a CLI program, and its already installed. Guess it came with Ubuntu.

---

### Post by cchhrriiss121212 on 2010-05-12
Jack has a good gui called qjackctl, which is in the repos. It also means you can use a variety of jack based audio programs like Ardour (very good for recording), guitarix (guitar amp simulator), rakkarak (fx processor) and hydrogen (drum sequencer).

---

### Post by Jammanuser on 2010-05-12
> **cchhrriiss121212 said:**
> Jack has a good gui called qjackctl, which is in the repos. It also means you can use a variety of jack based audio programs like Ardour (very good for recording), guitarix (guitar amp simulator), rakkarak (fx processor) and hydrogen (drum sequencer).
Thanks, both qjackctl and ardour were already installed.
I found a program called "JACK Control" under Applications->Sound & Video, and am assuming thats it. I installed Ardour a while back, but haven't really ever used it. I'll try using it in place of Audacity.

---

### Post by Jammanuser on 2010-05-12
Hmm...attempting to run Ardour resulted in the following message:

> Ardour could not start JACK

There are several possible reasons:

1) You requested audio parameters that are not supported.
2) JACK is running as another user.

Please consider the possibilities, and perhaps try different parameters.

I hit Ok, and it sent me to the "Audio Setup" page of Ardour - Session Control. Currently trying different settings.

---

### Post by cchhrriiss121212 on 2010-05-12
What you need to do is run jack first then open ardour, as a sound program cannot work without the sound server (jack) it was designed for. Open qjackctl then press the start button, which may result in an error message.

---

### Post by Jammanuser on 2010-05-12
> **cchhrriiss121212 said:**
> What you need to do is run jack first then open ardour, as a sound program cannot work without the sound server (jack) it was designed for. Open qjackctl then press the start button, which may result in an error message.
Thanks, its working now.
I will now see about recording from mic jack, and not from onboard mic.

---

### Post by Jammanuser on 2010-05-12
No luck. :(
Ardour doesn't appear to be recording either from the mic or from the jack.

I'll try some different settings.

---

### Post by cchhrriiss121212 on 2010-05-12
When using jack and Ardour you have to connect which recording source (capture) to which input in the connection bay. There is a program called patchage that gives a good visual representation of all your jack connections.

---

### Post by Jammanuser on 2010-05-12
> **cchhrriiss121212 said:**
> When using jack and Ardour you have to connect which recording source (capture) to which input in the connection bay. There is a program called patchage that gives a good visual representation of all your jack connections.
Ok, I installed and ran it, and the GUI started, but the following output appeared in the terminal:
> 
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
Failed to connect to LASH.  Session management will not occur.
Loading configuration file /home/gorilla/.patchagerc
Unable to load file /home/gorilla/.patchagerc!
SSE2 detected
Connecting to Jack... Done
Connecting to Alsa... Done
cannot read server event (Success)
cannot complete execution of the processing graph (Resource temporarily unavailable)
jack_client_thread zombified - exiting from JACK

That can't be good...

---

### Post by Jammanuser on 2010-05-12
But here is what it shows:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156659&stc=1&d=1273717223[/IMG]

---

### Post by cchhrriiss121212 on 2010-05-12
Ok, so jack/patchage is showing two capture devices which is a good start, capture 2 is likely the line in you want to use. To record in Ardour, you have to arm the track first and then press the main record button at the top of the controls.
I'm not sure about that error message, but I would ignore it for now as it seems to be running OK.

---

### Post by Jammanuser on 2010-05-12
> **cchhrriiss121212 said:**
> Ok, so jack/patchage is showing two capture devices which is a good start, capture 2 is likely the line in you want to use. 

Ok, but how do I use it?
> 
To record in Ardour, you have to arm the track first and then press the main record button at the top of the controls.

Yep, I figured that one out on my own. I pressed Shift + R to arm it, and pressed Space to start recording. However, no graphical lines or anything appeared on the track, when I tried to record my instrument through the mic jack, and after stopping the recording, then playing it back, I only heard silence on the other end, so I guess that means it didn't record. :P

---

### Post by Jammanuser on 2010-05-12
Ok, an update:

I think I changed connection from capture 1 to capture 2 through patchage.

Here's a screenshot:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156666&stc=1&d=1273720215[/IMG]

However, Ardour still wont record.

---

### Post by cchhrriiss121212 on 2010-05-12
Open a terminal and run alsamixer, which may indicate that the input is muted. Plus, when I use Ardour pressing space starts playback not recording.

---

### Post by Jammanuser on 2010-05-12
> **cchhrriiss121212 said:**
> Open a terminal and run alsamixer, which may indicate that the input is muted. Plus, when I use Ardour pressing space starts playback not recording.
Ok, I ran alsamixer, but I couldn't figure out how to use it. Its like a GUI that runs in the terminal, and responds only to key presses. I see something that looks like this:
> 
View: [Playback] Capture  All

and it appears to have Playback selected. However, using the arrow keys does nothing, except changes the graphical bar in the center.
I can't figure out how to go to "Capture", then adjust the input volume and input mute settings.

---

### Post by cchhrriiss121212 on 2010-05-12
Use f1 to see controls, f4 will display the capture channels. You should just be able to use right and left arrow keys to switch channels, then use up and down to set volume levels.

---

### Post by Jammanuser on 2010-05-12
Nevermind. I figured it out (read the manual).
I was able to get to the "Capture" section, however I don't see any input mute thing. I'm guessing the bar is for the volume. There were red bars at the top, so I turned it down to the first green bar. I did the same for both "Master" and "L   R
                   CAPTUR".
The manual says there should be an "M" under the volume bars when its muted, and a "0" under them when its turned on, however, there is neither under the "Capture" device's. As for the "Master", it shows "00" under the bar, so I'm guessing that means it turned on.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156670&stc=1&d=1273724219[/IMG]

---

### Post by Jammanuser on 2010-05-12
> **cchhrriiss121212 said:**
> Use f1 to see controls, f4 will display the capture channels. You should just be able to use right and left arrow keys to switch channels, then use up and down to set volume levels.
The arrow keys don't work, but thanks for the f4 shortcut. 

I was just typing this in the terminal:
```

alsamixer -V capture
```

or 
```

alsamixer -V all
```

or 
```

alsamixer -V playback
```

which opens up the device I want.

---

### Post by Jammanuser on 2010-05-12
Here is F2 alsamixer info:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156675&stc=1&d=1273724800[/IMG]

---

### Post by Jammanuser on 2010-05-12
> **cchhrriiss121212 said:**
> Plus, when I use Ardour pressing space starts playback not recording.
Yes, pressing Space alone starts playback. However, if you arm it first (Shift + R) then press Space, I think it records.
I got the shortcuts from the menu. I tried:

Shift + R

and then 

Shift + Space first, but nothing happened on the second, so that is when I just armed it first, then pressed Space, and it seems to record. But I could be wrong...

EDIT: Nevermind. I see. Pressing Shift + Space both arms and starts recording. So I don't why they have arm the record by itself (Shift + R).

EDIT again: But doing Shift + R then just Space still records too, though. Definitely.

---

### Post by cchhrriiss121212 on 2010-05-12
So you are still not getting anything recorded in Ardour? You should check that the signal going into the line in is at an audible level. Try connecting the capture straight to the playback channels that your speakers use.

---

### Post by Jammanuser on 2010-05-12
Update, 
I got the recording to work in Ardour. It seems there is one more thing you have to do to get it to really put stuff in the track: and that is to press a small button with a circle on it on the left side of the audio track. Once I did this, stuff is now being visually written on the track when I press Shift + Space and make noise.

However, its still recording from onboard mic instead of mic jack. :( And I can confirm that I tried it with Patchage showing only Capture 2 connected to Audio 1/in 1, and its still recording from the mic.

So it seems that no matter what I do, it still wants to record from my mic, which means when I try to sing along with my songs when I record, my voice gets recorded too, which I don't want because I want the vocals on a separate track.

---

### Post by Jammanuser on 2010-05-12
> **cchhrriiss121212 said:**
> So you are still not getting anything recorded in Ardour? You should check that the signal going into the line in is at an audible level. Try connecting the capture straight to the playback channels that your speakers use.
Read my last post for first question. As for the signal going into line in at an audible level, that's irrelevant as long as its still picking up audio data from the mic and not just from the jack. But I'll try that once I can stop the mic from picking up. 

In Volume Control, in the Recording tab, there is a "Front Mic Mixer" which I'm going to go ahead and either turn down or mute. Then I'll turn the "Line-In Mixer" up all the way, and try that. I'll let you know how it goes.

---

### Post by cchhrriiss121212 on 2010-05-12
> It seems there is one more thing you have to do to get it to really put stuff in the track: and that is to press a small button with a circle on it on the left side of the audio track. Once I did this, stuff is now being visually written on the track when I press Shift + Space and make noise.
This is what I meant when I said you need to arm the track, sorry as I should have made that clearer. And if capture 2 is recording the front mic, then maybe capture 1 is the line in.

---

### Post by Jammanuser on 2010-05-12
> **cchhrriiss121212 said:**
> This is what I meant when I said you need to arm the track, sorry as I should have made that clearer. And if capture 2 is recording the front mic, then maybe capture 1 is the line in.
Well, I tried both, and with either one, it still records from the mic providing the Options tag of the Volume Control: HDA Intel (Alsa mixer) has the following settings:

Digital Input Source: Digital Mic 1

Digital Input Source: (Any setting here wont affect recording from the mic)

and under the Recording tab, "Capture" has to be turned up, and the "Toggle audio recording from Capture" microphone icon cannot have a red x on it (if it does, it wont record from the mic). 

If I select the first "Digital Input Source" option as "Analog Inputs", when I try to record in Ardour with the guitar plugged into the computer through the mic jack, all that happens is Ardour draws a straight line (as opposed to wavy lines which it draws when im recording from the mic) across the line, which I'm assuming means it cannot pick up any audio data from the source. And that's with the capture volume turned up to 100/100 with alsamixer.

---

