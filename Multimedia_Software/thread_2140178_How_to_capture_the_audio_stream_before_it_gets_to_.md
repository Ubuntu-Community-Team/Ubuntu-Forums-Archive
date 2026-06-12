---
title: "How to capture the audio stream before it gets to the sound card?"
date: 2013-04-28
forum: Multimedia Software
---

### Post by Strelz on 2013-04-28
This probably sounds like a strange problem.  I am trying to figure out how to redirect all the audio sound stream that is headed for my sound card so that it will pass through my program first.  Then I will pass it to the sound card.

The application is a simulated hearing aid.  What I have working so far is as follows.  I take the audio input from my sound card and pass it through a digital filter of my own construction.  This filter is the hearing aid part.  My application includes a complete hearing test where I output a tone and record the threshold where it is heard.  I record this at many frequencies, and then load the required gains into my filter so that the the 'hearing aid' amplifies each frequency band by the appropriate amount.  I can then remove my own real hearing aids, and listen to sound input from my MIC without them.  I do this in stereo; there are two separate filters, one for each ear.  I can also switch from MIC input to a .wav file which I can unpack and play through my filter as well.

I am using C for the filter, and Python with Alsaaudio for the GUI and control parts of the program.  If you are wondering why I didn't use ALSA directly, the answer is that I got it to work, but found that Alsaaudio is easier to use.  So, I have a full duplex audio processing application that acts like a hearing aid.    But now, I want to capture any sound output.  For example, if the user is on Skype, or is listening to U-tube in a browser, or whatever, I would like to be able to insert my filter into the audio stream to make  a computer for the hearing impaired that does not require hearing aids (because they are inside the computer in my filter).  If I can get this working on my desktop, I plan to port it to Ubuntu phones.  Then you would have a hearing impaired phone.   Another aspect of this is that I adjust the gains in the filters so as to accentuate certain frequencies with the idea that this may provide some relief to Tinnitus sufferers (like myself).  

My problem is that I have no idea how to capture this sound stream within Unbuntu that is on its way to the sound card.  It requires a detailed knowledge of Ubuntu sound architecture which I don't have.  I'm hoping that someone who reads this can point me in the right direction.  If it helps, I am happy to provide more details of my application and the filter.  I intend to put the whole thing in open source when I get a little further.

---

### Post by zero2xiii on 2013-04-29
Hay,

I hate it when people do what I am about to do, but I will make this exception because I feel like you are trying to re-invent the wheel.

I suggest you port completely to JACK. Jack has everything you need to do EXACTLY what you want. Capture and redirect the input and output to different programs etc.

see [http://jackaudio.org/](http://jackaudio.org/) for details. It also has a nice API so I think it should be easy to port your program or add the API so it works as you intend it.

This would truelly be a very interesting program. As a audio engineer/sound engineer what you wish to call it, and having a dad with hearing aid this will be a very interesting project to follow. If you need some help testing or anything do PM me :)

Cheers

Just for some added information on audio in general in linux and ubuntu. See here: [http://tuxradar.com/content/how-it-works-linux-audio-explained](http://tuxradar.com/content/how-it-works-linux-audio-explained)
Maybe you might be interested in making it a more "permanent" part of the audio of the OS and then you should find out more on what leads to where so you can insert this tool there.

---

### Post by Strelz on 2013-04-29
Thanks Zero,

I will do what you suggest.  I did look at Jack and couldn't understand if it was what I needed or not.  It will take me some effort to figure it out, but your letter is very helpful, because now I know it is the right path.  If I get stuck in some way, I'll take advantage of your kind offer of help.

---

### Post by zero2xiii on 2013-04-30
Hay,

Glad I could give you a direction. If you want to experiment with the power and versatility of JACK without changing your current system, may I suggest you grab yourself a copy of [Ubuntu Studio]("http://ubuntustudio.org/") as it comes with JACK installed and configured out of the box along with a HUGE list of multimedia applications. I think this will be a great testing and experimenting environment for you. Unfortunately I do not think it has a live CD, only an install option so you will need to have either a virtual machine (suggested) or some free partition to install to. I do recommend the virtual machine option, it will make life just so much easier. There are a few free options, open box being one if memory serves me right... I use VMware for all my visualization.

Kind regards and good luck :)

EDIT:
Just saw in the download section it IS a live DVD so you can run it from the DVD or a USB stick. So you can test it out first before creating a virtual machine for actual testing and or using.

---

