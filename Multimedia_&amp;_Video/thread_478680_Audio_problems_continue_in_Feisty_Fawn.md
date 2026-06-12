---
title: "Audio problems continue in Feisty Fawn"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by jbag on 2007-06-19
Hi Guys

I am still having problems with getting the audio to work in Feisty. I know that maybe I should have posted it under the Comprehensive sound Problems Solution Guide, but my requests have gone unanswered so I thought I would try my luck here.

I have installed & un-installed the alsa drivers etc. & have followed the guide to the tee, but I am still having no luck. My sound driver is the via82xx.

Here is where I am right now:

My sound card right now is not being detected, although at first it was but just would not work.

I have all steps to the letter & am currently stuck in the section Alsa Driver Compilation.
                                                                                                                  Using alsa source

step 1: sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
      
      This part seems to go fine with no errors.

step 2: sudo dpkg-reconfigure alsa source

     As stated a big blue screen appears & the first 2 screens are fine however on the third screen
there is no way to select my driver, ie: no checkboxes. Screen looks like this

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring alsa-source &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Select the ALSA sound card drivers that should be included in             &#8593;  
 &#9474; alsa-modules packages that are built from the sources included in the     &#9646;  
 &#9474; alsa-source package.                                                      
 &#9474;                                                                           
 &#9474; The following is a list of available sound card drivers along with short    
 &#9474; descriptions.                                                              
 &#9474;                                                                           
 &#9474; seq-dummy (dummy MIDI-through sequencer client), dummy (dummy sound        
 &#9474; card), virmidi (virtual MIDI card), loopback (loopback card), ad1816a      
 &#9474; (ISA: Analog Devices SoundPort 1815|1816A chips), ad1848 (ISA: Analog     
 &#9474; Devices 1847|1848 / Cirrus Logic CS 4248 chips), adlib (ISA: FM card        
 &#9474; driver), ad1889 (PCI: Analog Devices 1889 (e.g. on HP PA-RISC               
 &#9474; computers)), ali5451 (PCI: AC97 codec on motherboards with ALi M5451        
 &#9474; Audio Controller), als100 (ISA: Avance Logic ALS 100|110|120|200 chips),  &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
    Any ideas why this is happening?

    What should I do next?            

  Hope someone can help!!!!

   Thanks

---

### Post by david_2001 on 2007-06-19
Not that I've been there myself but did you try selecting Ok and going to the next screen where, with luck, you would be able to pick your driver?  Thing is, the via82xx driver should just work without having to recompile alsa.  Find more information at [http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-via82xx](http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-via82xx).

---

### Post by jbag on 2007-06-22
thanks for the reply david_2001

Yes I did try to select ok from the screen but nothing happens.

Really strange

jbag

---

### Post by FloSynergy on 2007-06-22
hey there,

i'm having similar issues, so i've recently navigated the ui you are mentioning.

it's not designed very easy to use - if i remember well, freom the screen you are currently at, use the right cursor key to highlight the ok.

the next screen will allow you to select the module most appropriate to you....use the spacebar to mark or unmark, if my memory serves me (too much greenery, y'know...;-) )

give it a try and see if you can move forward.

all the best,

Flo

---

