---
title: "Full Screen ProjectM?"
date: 2008-12-06
forum: Multimedia Software
---

### Post by spacesearcher on 2008-12-06
I have a fresh install of 8.10 Ubuntu and I installed Amarok and Project M and when I try to click the maximize button then right click it acts like it is going into full screen adds black borders to the top and bottom then the go away in less than a second. I can't figure out why. Any Ideas?

---

### Post by krlhc8 on 2009-03-06
I tell you what.  There's a better way to install ProjectM.  I don't use the libvisual deal in Amarok; instead, I use the stand alone app.  It involves compiling from source, but it's worth it because you get to fullscreen and it actually works.  I can help you get it working if you want.  In the mean time, here are two tutorials for getting it to work:

[http://ubuntuforums.org/showthread.php?t=749793](http://ubuntuforums.org/showthread.php?t=749793)
[http://projectm.wiki.sourceforge.net/Installation+Instructions](http://projectm.wiki.sourceforge.net/Installation+Instructions)

Below is the ccmake configuration I used to get it to compile:

```

 BUILD_PROJECTM_QT_STATIC   OFF                                          
 BUILD_PROJECTM_STATIC      OFF                                          
 CMAKE_BACKWA...IBILITY     2.4                                          
 CMAKE_BUILD_TYPE           Release                                      
 CMAKE_INSTALL_PREFIX       /usr                                         
 DISABLE_MILKDROP_PRESETS   OFF                                          
 DISABLE_NATIVE_PRESETS     OFF                                          
 EXECUTABLE_OUTPUT_PATH                                                        
 INCLUDE-NATIVE-PRESETS     ON                                           
 INCLUDE-PROJECTM-JACK      OFF                                          
 INCLUDE-PROJECTM-LIBVISUAL ON                                           
 INCLUDE-PROJECB...-ALS     OFF                                          
 INCLUDE-PROJECT...UDIO     ON                                           
 INCLUDE-PROJECTM-QT        ON                                           
 INCLUDE-PROJECTM-TEST      ON                                           
 INCLUDE-PROJECTM-XMMS      OFF                                          
 LIBRARY_OUTPUT_PATH                                                           
 QT_QMAKE_EXECUTABLE        /usr/bin/qmake                               
 SDLMAIN_LIBRARY            /usr/lib/libSDLmain.a                        
 SDL_INCLUDE_DIR            /usr/include/SDL                             
 SDL_LIBRARY                /usr/lib/libSDLmain.a;/usr/lib/libSDL.so;-lpt
 USE_CG                     OFF                                          
 USE_DEVIL                  OFF                                          
 USE_FBO                    OFF                                          
 USE_FTGL                   OFF                                          
 USE_GLES1                  OFF                                          
 USE_NATIVE_GLEW            OFF                                          
 USE_OPENMP                 OFF

```

Any questions, just holler!

---

### Post by spacesearcher on 2009-03-06
Well some how it started working with out doing that. thank you for your help though :) 
When you use this standalone app though how does it work? Like could it work with flash audio like pandora.com since it isn't using an audio player?

---

### Post by krlhc8 on 2009-03-07
Exactly.  It takes whatever audio is being played by the computer from the pulse audio sound server and will visually represent it.  It is better than the libvisual guy you use in Amarok because it has its own interface where you can make a milkdrop visual playlist and change preferences.  I posted a screenshot.

---

### Post by spacesearcher on 2009-03-08
Ok I'm trying to install it right now. I'm following the instructions I am doing the second option in the instructions and I got to the part where you do ccmake . and I can go through and change the options to what you used. I then hit 'g' then 'q' and type 'make' and it says "make: *** No targets specified and no makefile found.  Stop." 

I am in the src directory of projectM-Trunk. I also tried to press 'c' when in the ccmake screen and it gave me the error: 

" CMake Error at projectM-pulseaudio/CMakeLists.txt:44 (MESSAGE):
   ERROR: Pulse Audio is NOT found.  Please install pulse audio 0.9.8 or
   greater from www.pulseaudio.org." 

However Synaptic Package Manager says I have pulseaudio installed with the version being 0.9.10-2ubuntu9.3 and libpulse-dev installed. what am I doing wrong?

---

### Post by spacesearcher on 2009-03-08
ahhh!!! wait it started working randomly!!! but how did you get the screen with the playlist on the upper left hand of your screen shot???

---

### Post by spacesearcher on 2009-03-09
Oh and I am noticing much lower quality. like the glow stick visualizations aren't all smooth, fluid and rounded like they are in amarok. when using project m without amarok they have square edges and like sharp corners. is this a setting in here i can't figure out why it would be different i have played with the quality settings going both up and down and nothing is helping.

---

### Post by krlhc8 on 2009-03-10
Push the "M" key on your keyboard for the menus, and push "F" key for fullscreen.  I attached my settings to this reply; take a look.

---

### Post by spacesearcher on 2009-03-10
Cool. You wouldn't happen to know why some of the visualizations are behaving differently than they did with amarok would you? like the glowsticks variations instead of being all fluid and round and flowy they have straight edges sharp corners and eventually stop responding to the beat. that's the only issue I am having now.

---

### Post by krlhc8 on 2009-03-11
Tell me more about your computer.  Maybe we can up the settings.

---

### Post by spacesearcher on 2009-03-11
Nvidia 8600M GT
Intel Dual Core @ 2.4 GHz
1440 X 900 Display
But i think i figured it out by enabling the Use GC and using the milkdrop 200 presets instead.

---

