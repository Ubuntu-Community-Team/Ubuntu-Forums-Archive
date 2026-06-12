---
title: "electric guitar - ubuntu 14.04 from scratch"
date: 2015-01-31
forum: Multimedia Software
---

### Post by Claus7 on 2015-01-31
Hello,

I would like to post some steps that I followed in order to "match" ubuntu with an electric guitar. I was (and still am) a complete noob to to the subject, and this is the perspective this "how to" will follow.

1) I would like to buy a guitar, is there more than one type available?

Yes, there are (in general) 3 types of guitars: acoustic, classical and electric. You might find out more types like banjo for example, yet I won't discuss about these instruments.

With the classical guitar someone will be willing to play the melody (solo) whereas with the acoustic just the chords.
With the electric guitar someone can do both. Also the electric and the acoustic have smaller (thinner) neck so for someone with not long fingers will be easier to start with.

2) I would like to buy an electric guitar. Will it work without electricity?

Yes it will, yet the sound won't be so loud. Also the various buttons that this guitar will have won't work if this is not plugged in to an amplifier which will enhance the sound of the electric guitar.

3) I know that the basic notes of the piano are: do re mi fa sol la ti do. How about the guitar?

For start the guitar has 6 strings. Starting from the top one (the one with the deepest sound) this corresponds to the note mi. Then la re sol ti mi.

[IMG]http://hatexsindo.com/upload_files/guitar-string-notes-standard-tuning.jpg[/IMG]

4) Is there any other notation about notes?

Yes this is the correspondence:
do: C
re: D
mi: E
fa: F
sol: G
la: A
ti: B

5) How will I recognize the notes using the guitar?

Check my attachment which shows which note will sound by pressing the right note at the right fret.

6) What has ubuntu to do with electric guitars?

I wanted to connect this electric guitar to my ubu box. In order to do that you will need:
i) one cable which will be like:
[IMG]http://i01.i.aliimg.com/wsphoto/v0/2050971169_3/1-8M-Length-Jack-6-35mm-Male-Plug-Guitar-Audio-Cable-Amplifier-Patch-Cord-for-Electric.jpg[/IMG]

which is a male to male 6.35mm or 1/4 inch cable

ii) and a jack 6.35mm female to 3.5mm (1/8 inch) male (golden is better for stereo support):

[IMG]http://www.egoodeal.com/images/IE00088.jpg[/IMG]

and the male part will be placed in the "line" input of your sound card (usually blue color):

[IMG]http://www.homebrewedmusic.com/media/2012-05-03-soundcard/soundcard.jpg[/IMG]

7) In order to hear sound while you are playing the guitar you should install the following packages:
(these were downloaded and worked for me, there are other options as well)

> i) rakarrack
ii) qjackctl (for this package I have installed jackd and jackd2)

8) You should open rakarrack and check if you can hear sound from your speakers. Still I cannot hear sound, what is the problem?

If you hear no sound or you hear sound from some of your speakers, then you should open and configure qjackctl as well and connect the left hand side part (after you expand it) with the right hand side part. You can experiment with inputs and outputs to check which one is ideal for your system.

[IMG]http://farm9.staticflickr.com/8053/8085957543_213a56f503.jpg[/IMG]

playback#: are (also) the speakers you have

9) I hear some noise from my speakers, how can I get rid of it?

Usually unchecking the "FX on" option on the top left hand side corner of rakarrack will do the job. Also changing the "present" option (top in the center) will give you different sounds as well, which you can save in the end. 

You can also use audacity with rakarrack in order to record what you want to play from your guitar.

10) I'm done with my performance. I want to close rakarrack and enable sound as it was before.

If you open rakarrack you will notice that you won't be able to listen to other sound from your computer. Even if you close rakarrack sound won't be enabled by default. You should:

i) either ps ux | grep jack and kill the process which runs jackd along with alsa:
kill -9 number_of_process_with_jackd_alsa
edit: and also issue the command: pulseaudio --kill
or
ii) 
In Jack Settings Window, click on 'Misc' tab and make sure

'Enable D-Bus interface'

is unchecked

from: [http://ubuntuforums.org/showthread.php?t=1895430](http://ubuntuforums.org/showthread.php?t=1895430), (edit)which has not worked for me

If firefox is running, close it and open it again. Also if you still have not sound, go to your sound options and check if your speakers are working by testing them.

Hope it helps,
Regards!

---

### Post by MartyBuntu on 2015-02-01
I'd recommend you running your patch cable into a guitar/mic pre-amp and then into your LINE IN or MIC on your computer.

---

### Post by monkeybrain20122 on 2015-02-01
Interesting post. Thanks for sharing. :)

---

### Post by Claus7 on 2015-02-04
Hello,

> **MartyBuntu said:**
> I'd recommend you running your patch cable into a guitar/mic pre-amp and then into your LINE IN or MIC on your computer.

thank you for your recommendation. I have seen that people say that this improves the quality of the sound, yet the sound I'm getting up to now with the configuration I described is descent. 

> **monkeybrain20122 said:**
> Interesting post. Thanks for sharing. :)

glad you found it interesting!

Regards!

---

