---
title: "How can i get started with Ubuntu Studio?"
date: 2007-07-14
forum: Multimedia Production
---

### Post by volksolwagen57 on 2007-07-14
I have been playing guitar for a few years and i've always wanted somekind of recording studio. i haven't heard a lot about the different software available; if one is better than the other. so now i've got ubuntu studio. i've got a few questions:
1. do i treat the multimedia codecs the same as in ubuntu feisty?
2. what other codecs or repositories do i need to get most of the recording software working?
3. what kind of sound card would anyone recommend to enable use for a preamp and microphone.
4. what kind of microphone does anyone recommend (i plan to record one track at a time)
i know that it's a good idea to record at different areas on a guitar, for example, record one track for the bridge for low end or the sound hole, one track on the neck for middle range, and one track by the headstock.
5. does anyone have any recommendations?
i appreciate all your help in advance.

---

### Post by robertc36 on 2007-07-14
Hi not gonna answer all your questions but i presume you mean recording an acoustic.
When recording guitars i always record the amp.
Literally stick microphone in front of amp.
Recording acoustic i position the mic at the end of neck just above soundhole.
So i dont get too much of the pick hitting the strings, you have too leave yourself room to play lol.
I am probably wrong but this gets the best results for me.

---

### Post by nalmeth on 2007-07-14
1. Yep
2. Enable the ubuntustudio repositories for when you need them, but I wouldn't recommend installing everything if you just have the regular Ubuntu 7.04. If you're using the binary Nvidia/ATI drivers, don't install the linux-lowlatency kernel.
3. Check this [link]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Main") for cards and their compatibility
4. Go to a guitar store somewhere around your home, and pick up a live mic, it'll have a 1/4 inch jack. For a generic soundcard you will also need a 1/4 inch -> 1/8 inch jack adapter. 
5. Install qjackctl (to start and control the jack audio system), and ardour2 (a multi-track recorder and editor).

In Ardour you have to add a track, and then arm it for recording. 

Start with those two apps and go from there!
Any questions, just shoot

---

### Post by peterkirn on 2007-07-15
I'm a bit confused on that ... is there in fact no way to use the NVIDIA binary universal driver with the linux-lowlatency kernel? (Assume the kernel interface from NVIDIA is incompatible?)

What's the preferred installation method? To be honest, 3D capabilities are significant to me, so I'd ideally want to keep the NVIDIA drivers around ... is it possible to maintain separate xconf.org files, so the generic driver loads with the lowlatency kernel and the NVIDIA binary can be loaded without? (Right now, I tacked on ubuntu studio atop a 7.04 install, which left a lowlatency install that breaks and a normal kernel grub option that works fine...)

Apologies for being dense on this ... would be great to formalize the documentation here.

Peter
[http://createdigitalmusic.com](http://createdigitalmusic.com)

---

### Post by michaelwilliamson on 2007-07-15
I'm using the Nvidia driver and the low latency kernel. I've had a few issues here and there, but figured it was me being a newb.... The two don't sound like they should be connected, so why wouldn't you use the two together? 

sounds curious?

---

### Post by nalmeth on 2007-07-16
I've heard that the lowlatency kernel can be used with binary video drivers, but on every machine I've tried, it crashes X. So I just throw it out there so people aren't totally surprised if it happens. 

I don't especially recommend the lowlatency-kernel if the binary drivers don't work, I don't get any better performance with it over the generic kernel. Maybe others would disagree with that.

If latency really becomes a problem for you, you should install a realtime-kernel, or a distro that uses one.

EDIT:
> I'm using the Nvidia driver and the low latency kernel. I've had a few issues here and there, but figured it was me being a newb.... The two don't sound like they should be connected, so why wouldn't you use the two together? 
 
 sounds curious?
A lot of kernels patched for latency/pre-emption are patched without headers required to run binary video drivers. 'Binary Blobs' that let the kernel communicate with the closed-driver. So binary video drivers will not run, but the FLOSS nv or ati drivers will still work. I understand the lowlatency-kernel was built with the headers, but they didn't work in my experiences.

If that is unclear, maybe a more knowledgeable kernel guru can explain

---

### Post by peterkirn on 2007-07-16
Okay, so at least I know it's not just me crashing X with the lowlatency kernel. ;)

Now just have to edit my grub boot so it stops trying to load it ... and do some other testing. Any more scientific way to test latency, incidentally?

ALSA + JACK seems perfectly happy here. It's funny, because I keep hearing people griping about general-purpose distros for audio, but the kernel seems not to really be the major issue (other stability issues being far more what people would worry about in everyday use, particularly as a place to start for beginners).

Thanks for the tip ... had to at least ask why you were throwing that out.

---

### Post by zettberlin on 2007-07-16
Hello,

regarding the NVIDIA-issues: just install the lowlatency-kernel and make sure, that thr restricted-modules for this kernel are installed as well. Then you could reinstall/reconfigure the proprietary NVIDIA-Drivers with synaptic and everything should be OK (as it is for me on dozens of Installations ....)

> **volksolwagen57 said:**
> I have been playing guitar for a few years and i've always wanted somekind of recording studio. i haven't heard a lot about the different software available; if one is better than the other. so now i've got ubuntu studio. i've got a few questions:
1. do i treat the multimedia codecs the same as in ubuntu feisty?
.
Yes


> **volksolwagen57 said:**
> 

3. what kind of sound card would anyone recommend to enable use for a preamp and microphone.


I recommend a card with envy24-chipset, such as MAudio Audiophile or Delta-models. USB-Boxes with that chipset should work as well. My machines arre used for exactly the jobs, you mentioned - I record evverything, that comes thru a microphone via a small mixingdesk (Mackie-Clone), that is connected to the IN-jacks of the soundcard.

---

### Post by skipkent on 2007-07-16
Soundcard:  Seeing as your just exploring, work with what you have.  The built-in 16-bit soundcard on your motherboard is PLENTY to get you started, I don't care what anyone says.

Microphone:  Go to your local music store and you'll have plenty to choose from (new and USED) around $50 or less.  I would suggest a cheap dynamic mic for starters.  Save the shock-mounted condenser for later after you know your way around the software.

Mixer:  Get a cheap Behringer (or whatever) mixer to plug the mic into.  Plug one (or both with a Y cable) of the send outs of the mixer into the Line In of your soundcard.  Plug the line out of the soundcard into one of the stereo tracks of the mixer.  Plug your headphones into the mixer and theres your basic setup.

This way, you can plug your guitar (or mic) into the mixer and then adjust the level going to the recording app (Ardour/Rosegarden/whatever) without having your monitoring of your other tracks getting recorded as well.

Yes, a mixer is a bit of an expense, but it's totally worth it because you will be using that a lot from this point on no matter what os/software platform you take on as the one for you.  I personally think your money is better spent here at first than on a fancy sound card, but then again the fancy (usb?) sound card can often be used without a mixer, so whatever feels right to you is the way to go.  Mixers are just so darn useful to have around; with one, you'll never be at a loss for xlr inputs or phantom power or whatever regardless of were the signal goes from there.

As far as recording and mic placement, you've got enough on your hands getting started as it is.  For now just record anything any way you can and get to know how things works.  Linux is not as intuitive or easy at first as Cubase or Tracktion or whatever running on windows, and there will be a lot of head-scratching and maybe even some swearing before you get familiar with things enough to sit down and record ideas instead of sit down and try to figure out HOW to record your ideas (if that makes any sense ; ).  

I will say that, as tracks build up, low-shelving is your best friend.  Shaving a bit of the low-end off of just about everything (especially accoustic guitar) can really help to un-mudd-ify a mix.  The guitar should sound almost 'too thin' when you solo it and then it will fit in nicely when mixed with a bass guitar/voice/drums whatever.  Shave a bit off of vocals too, as they can make for a boomy (not in a good way) mix if not tamed a bit.

Be patient, keep going and have fun!  Let us know how you make out.

---

### Post by nicholaspaul on 2007-11-13
As far as recording acoustic goes, the best thing to do is experiment. Having two mics is a bonus, as is an onboard preamp (yea, I know they don't sound amazing, but still ... use it!)
Getting an inexpensive condenser is a great plan. My Apex works wonders on vocals and acoustics. Also, if you get a Shure SM57 (or equivelant - every manufacturer including Apex makes a Shure copy) you'll be set. The SM57 is a classic mic that you can use on EVERYthing. 
Now comes the pointing - as someone already said, point one mic (I use the condenser) at the end of the fingerboard, somewhere between fret 12 and the end. The other mic can be aimed at the body (upwards from the floor) for lovely bottom end, or at the bridge for nice attack. If you have a particularly nice room, you can aim it a little further away to get some fab reverb. 

Now with the multitracker, you can mix each of these recordings. Mix in the percussive high end tones of the piezo pick up too. Add reverb in different amounts to each one. Also, cutting everything below 250Hz and taper off after 400Hz, just to keep the low rumble out of the picture. 

A nice preamp can really help too. Use a tube guitar pre, or a regular mic preamp to beef up the sound. 


PS Yup - a mixer is a must have. it makes plugging in two or three instruments way easier, even if you are recording alone.I have a Yamaha 10 channel which was only slightly more expensive than the Behringer, but has way better preamps. I use two mics regularly, one channel (stereo) for electric guitar and another for drum machine. That leaves some room for adding a bass, external guitar processor or whatever else I have around. 

Anyway, those are my thoughts and experiences. I can get some pretty decent acoustic tones this way.

---

### Post by kayosiii on 2007-11-13
1 & 2) Think of Ubuntu studio as Ubuntu with a realtime kernel (in 7.10) & a different colour scheme and most good Open source Audio/Video/Graphics software installed by default. you shouldn't need a lot in terms of extra software for doing sound other than the usual mp3/DVD playback stuff. 

3) I am using a presonus firebox and am very happy with it - there is one small hack needed to get it to work with Ubuntu-studio (changing the default ownership of the raw firewire device). Sound Quality is fantastic and has professional quality preamps built in. Soundcard cost me about $500 Australian.

4) I am using a pair of MXL's that I got in a kit for $360 australian - the 2003 and the 603/s. The 2003 in particular is crazy sensitive - I can sometimes pick up noises several houses away. These get really good sound. When recording guitar I use one pointed at either the place where the neck meets the guitar or halfway between the soundhole and the bridge. The second mic I place further from the guitar to pick up more of a room sound.

5) Join the Linux Audio Users mailing list or search the archive you will find a great many question you have will have been discussed in great detail.

---

### Post by Drunky on 2007-11-14
+1 Shure 57

---

