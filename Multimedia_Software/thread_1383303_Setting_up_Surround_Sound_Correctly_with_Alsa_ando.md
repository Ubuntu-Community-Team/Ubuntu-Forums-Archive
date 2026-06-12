---
title: "Setting up Surround Sound Correctly with Alsa and/or Pulseaudio"
date: 2010-01-17
forum: Multimedia Software
---

### Post by sports.car.guy on 2010-01-17
[U][SIZE=4][B]Still in progress:
[/B][/SIZE][/U] 
Hello Everyone,

The reason why I have created this post is because I have encountered so many issues and shortcomings with the mixing of channels and surround sound when it comes to Linux, and not due to the software. It is due to lack of documentation, and it is far from funny. Up-mixing, down-mixing, and Surround sound have been around in the PC world for quite some time, and no one regardless the operating environment has truly got it right. 

There are things that need to be looked at when setting up any surround sound system, whether it is on a PC such as this tutorial covers, a home theater which this type of setup could cross over into thanks to software like MythTV, or any other similar endeavor. This tutorial will address as much of everything as humanly possible in relation to proper setup on a Linux PC.

This was tested on two Kubuntu 9.10 machines of mine and should work on any Linux system with little to no modification. In order to best understand what this tutorial / howto is showing some background in audio reproduction is necessary. The next section gets you up to speed on what you need to know in relation to audio reproduction.

[SIZE=3]_**Audio Reproduction 101:**_[/SIZE]

When we hear sound, nature empowered us with the ability to distinguish where it is coming from through depth using two auditory receptors, our ears. Similarly to eyesight and depth perception, we are able to distinguish the relative distance to where a sound is coming from due to our ability to hear in stereo. This ability led to the development of stereo audio and eventually surround sound.

Surround sound is more then just piping audio to speakers carelessly placed around the area where someone will be sitting in a room, and having audio coming out of all of the speakers pounding on them. There are three things to a proper setup, staging, frequency filtering to the speakers, and the ability to use an equalizer, all in order to tweak the sound and get the best from your hardware. Too often these are never really looked at in the PC world and should be, especially if the system is used primarily for multimedia and home theater applications.

_**What is staging?**_

Staging is the layout of your speakers in the environment to put it simply, but there is much more to it. It also involves how sound is presented to a person in the audio environment. In the placement of speakers, things like the height they are placed at, the direction they are facing, and distance play a big part in the environment. More often then not, no room provides the ideals for speaker placement, but they usually provide good enough to get pseudo ideal through some tweaking.

The need for tweaking is to address things like out of phase audio. When audio is out of phase in a surround sound system it can really mess with auditory perception of a sound's location and depth perception of it. It can cause an echo effect and actually effect the reproduction of sound from the other speakers as well. Perceptually what happens is the sound waves deflect away the sound from other speakers or even cancel it out.

Having the speakers in as close to ideal locations, the only way to fix issues with staging such as out of phase audio is to adjust the timing on when the sound is reproduced by the speakers that are out of phase. Almost every home amplifier / receiver that does surround sound has the capabilities to make adjustments the timings of speakers in order correct phase issues, and Linux does as well using Alsa. Most never use this capability though on their home audio systems or computers. That should not be the case though.

The capabilities are there to make the experience the best it can possibly be through fine tuning, because the physical staging (layout) of your speakers has the experience just being okay and falling short, you just need to get it that little bit further. Correcting a surround sound environment is not rocket science, it's auditory perception, and not as remotely complicated as rocket science either or even as much as you might think. Now that you know the basics of staging it is time to look at the need for proper frequency cut offs, and with both, from there get into implementing them with strictly Alsa or with a combination of Alsa and pulseaudio.

_**What are Proper Frequency Cut Offs?**_

There is more to just staging when it comes to accurate and auditory pleasing sound. There is the need to make sure that only the frequencies necessary for an accurate sound field are sent to each speaker as well. This also can play a big factor into a speaker's longevity besides having great sound reproduction. We do want our investment in those nice surround speakers to be a long lasting one, and maybe milk it for as long as we can. Especially so with how the economy is these days.


Anyone familiar with aftermarket car audio beyond just putting a deck into the dash should understand the contents of this section, even home audiophiles too, but it still needs to be addressed for those out here who have never had to deal with frequency cut offs like the majority of people in the world. There are three factors to proper frequency cut offs which need to be looked at here before getting into combining everything and getting our hands dirty setting things up.

The first factor are the speakers being used in one's surround sound environment. This one is the biggest to consider in the proper frequency cut off equation and needs to be looked at with some attention to the details. In designing speakers there is what a speaker is physically capable of reproducing for frequencies and ideally what it should be reproducing, and both are far different from each other. Not properly setting limits on what is sent to a speaker can at minimum make the quality lacking, at most it can lead to the premature failure of the speaker, you know when you have blown it out and it sounds kind of like a wet fart.


A good example for speakers and what frequencies are sent effecting reproduction is the sub-woofer. It is designed to reproduce bass and only bass. The way bass works is it only truly sounds like it is part of sound field coming from a directional speaker such as the center channel in a surround system when the sound is coming from that speaker, otherwise it is not perceivable where the bass is coming from. Bass in general is good for all sound reproduction, like when the sub-woofer is set off to the side so to speak.


The reason a sub-woofer can do this is because with bass, we are unable to tell the direction it is coming from by itself. That is when it is reproducing frequencies about 100Hz and lower. When it is being reproduced in conjunction with the higher frequencies on another speaker or speakers it blends in and we then find it to be directional perceptually. If the cut off for lower frequencies being sent to the sub is too high, this does not happen and can greatly effect staging. The environment also has a factor in setting proper frequency cut offs.


A room can greatly effect the reproduction of sound. The use of proper cut off frequencies can help address this. The reason it happens is because of the layout of a room, such as size, furniture in it, shape, the materials it is made of such as sheet rock or wood paneling, and so on. A room can be conducive to the reproduction of bass and because of this there may be a need to lower the frequency cut off of the signal to it.


Finally there is the means of setting a proper frequency cut off. This is probably the least understood by some. The general thinking is the set cut off point is exactly where the frequency is cut off. That is so far from the actual reality of things and no one generally has a clue this is not the case. How high and low pass filters work, regardless if they are done in software or hardware using integrated circuits or tubes  have the frequency range actually goes past the point of where it is cut off. It is a small amount but needs to be accounted for none the less when setting a cut off for frequencies.


At the tiime when people referred to low, high, and mid pass filters as crossovers, they understood this concept. It is from that time this actually carries over even today. The reason this is the case, goes back to the days of vacuum tubes. Tubes were used in these filters and did not have the capability to cut a frequency at exactly a particular Hz and not have bleed over. By setting a low and high, or low, mid, and high pass filter slightly apart in an ideal environment they bled into each other making for accurate reproduction. This continued into the electronics age now the software age today.


Both of these means are capable of cutting a frequency to a fraction of a Hz exactly but don't and this needs to be accounted for when setting up a proper frequency on your filter.

Once proper low and high pass filters are set for the speakers, adjusting frequencies isn't over. The addition of a graphic equalizer to the output brings everything all together. Each speaker is getting the ideal frequencies to it, but combined the sum of the audio will still need the benefits of EQ frequency tweaking.

Environment will cause for some frequencies to become overpowering while others fall short, and that is where an EQ helps. Most think to add boost to frequencies with an equalizer and the opposite should be considered as well.

Everything covered so far will get laid out in detail as we progress further. The first thing to cover is up-mixing and down-mixing of audio. Without either, we would not get the most out of our speakers and get to enjoy sound coming over all of them when in use.

[SIZE=3]_**Up-mixing and Down-mixing to Produce or Alter Multiple Audio Channels:**_[SIZE=2][SIZE=1]
[/SIZE][/SIZE][/SIZE]
The first thing we need to look at is why would someone want to up-mix or down-mix an audio track, file, movie, etc. There are a lot of reasons. Like for stereo in an audio file or move, we want to hear our sound coming over all our speakers and have more immersion into it. Another reason is when there are more tracks then speakers available. It even applies to when using headphones.

There are a few different ways to enable this feature with Linux. Two of them personally I find to be very lacking. They lack flexibility or control. One is the default for pulseaudio when enabling it use of more then just 2 speakers. When you enable pulseaudio to use more then 2 speakers it will automatically up-mix and in theory down-mix all audio sent to it. There is no fine tuning to levels, timings, etc, no configuration at all. Alsa too has a similar feature.

With Alsa, it's up-mixing capabilities are lacking due to how it is implemented. Alsa duplicates only one channel, the left front for center and the sub-woofer, no combining of stereo into a mono channel. This could be the way pulseaudio does it as well and I am not sure as of this writing if it does. It is how Windows probably accomplishes it was well.

People comment about how it just works in Windows. That is such BS, it still has to be enabled and we are talking Microsoft here. This is probably one of the most nasty implementations of up-mixing and down-mixing in the PC world in comparison to options available on other operating systems. Just because something works in Windows does not mean that it is implemented right. The same is true the two ways to have this working under Linux, but they are enabled just as easily and quickly as Windows concept of up-mixing and down-mixing. Both of these are truly quick and dirty way to get up-mixing and down-mixing working.

[SIZE=2]_**Quick and Dirty Up-mixing and Down-mixing:**_[/SIZE]

Saying that these two ways to handle up-mixing and down-mixing are the quick and dirty ways does not mean they are really the wrong way to do it. Literally it is the quick way regsrdless of the one chosen. Then how this capability is implemented is definitely not the cleanest way, especially when it comes to the listening experience, and that is the dirty part.

**[FONT=Arial]*[SIZE=2]_PulseAudio:_[/SIZE]*[/FONT]**[SIZE=2]
[/SIZE]
As a choice this is not the best one in my opinion to use. I truly don't understand why all these distributions have embraced it. The Edsel was in theory a good car, but doesn't mean in reality it was. Don't see Ford selling the brand anymore do you, and that is what should happen to with this technology.

It was never designed to be a real time sound service or layer. There is way too much overhead with it, never mind the network latency issues. It shines as a means to control sound over a network remotely, such as streaming to speakers music from another room, and that is about it's only redeeming quality. Lets look at how to enable up-mixing and down-mixing with pulseaudio, which subsequently turns on the speakers for surround as well.

First you need to edit the daemon file for pulseaudio:

  	 	 	 	 	 	  sudo kate /etc/pulse/daemon.conf

or

sudo gedit /etc/pulse/daemon.conf
 
Once you have it opened scroll to this line and uncomment it along with set speaker count:

  	 	 	 	 	 	  From this:
;default-sample-channels = 2

To this:
default-sample-channels = 6
(This is for a 5.1 setup. If it is 7.1 it would be 8 for the count.)

 
To have everything take effect you can restart the pulseaudio service, but I strongly suggest a reboot with it. Now up-mixing, down-mixing, and all your speakers should be working. That is all there is to it with pulseaudio.

  	 	 	 	 	 	  To test that you have surround working issue the following command in a terminal:

jschmoe@example:~$ speaker-test -c6 -twav

To test upmixing:

Open a stereo or mono mp3 or another type of audio file. It should now be heard over all speakers.
 

People make it sound like it is so complicated to get these features working with Linux and it took about the same time as if enabling on Windows, go figure. Time to look at how Alsa does it the quick and dirty way.

**_Alsa:_**

I have never personally tested this method, but everything indicates it will work. I will not swear to it or give any guarantee it will. In my trying to get this all setup and working to it's potential, surround and up-mixing, I came across this method and was surprised to see Alsa had a similar way to get it up and running to how pulseaudio does. The beautiful thing about Alsa is no need to reboot to get this to work, just restart the application you are using.

The code snippet to enable up-mixing and down-mixing can be placed in one of two locations. One only effects a single user, the other implements it globally across the system. 

(You may have to create the files yourself.)

Single User:

sudo kate ~/.asound.rc

sudo gedit ~/asound.rc

Global All Users:

sudo kate /etc/asound.conf

sudo gedit /etc/asound.conf

Place this code inside the file:

pcm.duplicate {
type plug
slave.pcm "surround51" #Note this will be whatever your 5.1 device is.
slave.channels 6
route_policy duplicate
} 

Once this has been placed in either file run the same tests as to see if it works with Alsa by starting a stereo mp3 for playback. Everything should be all set now.

_**Up-mixing and Down-mixing with More Control:**_



[SIZE=4]_**To Be Continued...**_[/SIZE]

---

### Post by AHD on 2010-08-01
Hi there, 

came from here: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9664468#post9664468](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9664468#post9664468)

you are not the only ones having issues with proper sound output...
The best sound I ever had was with an audigy2 card using foobar with it's nice decoder/matrix mixer plugins. There you can even let it calculate the delay in relation to the distance of the speaker. Also the frequency cutoff options helped getting rid of these "phase cancelling things" ;) ...did it without knowing rocket science just tried every possible combination. The trick is to mute the sound for some time and then switching between the settings. These ears are easily tricked.

Regards,
Alex.

---

