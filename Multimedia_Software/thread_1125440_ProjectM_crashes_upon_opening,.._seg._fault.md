---
title: "ProjectM crashes upon opening,.. seg. fault"
date: 2009-04-14
forum: Multimedia Software
---

### Post by tigerrider11 on 2009-04-14
Hey everyone, 
I have been trying to get projectm-pulseaudio to work on this computer for some time now. I had it working on my other computer through amarok, but I cannot for the life of me get it to work on this one. When I open it from the applications menu, it opens for a split second, then terminates, and the same happens when I try to access it though the visualizations tab in amarok. 
When I try to open it through the terminal, this is what it responds with.  
The segmentation fault get put out at the same time the window opens for a split second and crashes: 
 
jon@jon-desktop:~$ projectM-pulseaudio 
dir:/usr/share/projectM/config.inp  
reading ~/.projectM/config.inp  
[projectM] config file: /home/jon/.projectM/config.inp 
No Textures Loaded from /usr/share/projectM/textures 
set pipeline broken FIX ME 
[projectM] Allocating idle preset... 
[PresetFactory] path is Geiss & Sperl - Feedback (projectM idle HDR mix).milk 
[PresetFactory] url is idle://Geiss & Sperl - Feedback (projectM idle HDR mix).milk 
[projectM] warning: no valid files found in preset directory "" 
call factory clear here? 
call factory clear here? 
unconnected: connecting...  
connectHelper: "alsa_output.pci_8086_24d5_sound_card_0_alsa_playback_0.monitor"  
Segmentation fault 
 
does anyone have a clue how to fix this?? 
thanks, 
-jon

---

### Post by Psychopump on 2009-04-15
*bump*

Same issue...Any ideas?

---

### Post by tigerrider11 on 2009-04-16
hey, i figured it out finally
::
go into synaptic, and type: libproject  into the search field
-you should see some options, i saw 4, libprojectm2 (selected); libprojectm1 (not selected); libprojectm-dev (not selected, but it should be, so select it to install and then apply the changes); and libprojectm-data (already selected for me)...
just make sure the dev package is installed and it should work, mine is incredibly slow right now but i think thats just because i have a ton of programs running and only 512mb of ram...
hope it works for you

---

### Post by Psychopump on 2009-04-21
> **tigerrider11 said:**
> hey, i figured it out finally
::
go into synaptic, and type: libproject  into the search field
-you should see some options, i saw 4, libprojectm2 (selected); libprojectm1 (not selected); libprojectm-dev (not selected, but it should be, so select it to install and then apply the changes); and libprojectm-data (already selected for me)...
just make sure the dev package is installed and it should work, mine is incredibly slow right now but i think thats just because i have a ton of programs running and only 512mb of ram...
hope it works for you

I did this, hoping it would help me too...
Unfortunately, it has not helped at all.
Now, I don even get the instantly-opening-and-closing window anymore, I try to start ProjectM and absolutely NOTHING happens...

Please can anyone help?

---

### Post by adam_kimber on 2009-05-02
I get some other weird problem about lack of textures?? :confused:

```
$ projectM-pulseaudio
dir:/usr/local/share/projectM/config.inp 
reading ~/.projectM/config.inp 
[projectM] config file: /home/adam/.projectM/config.inp
No Textures Loaded from /usr/local/share/projectM/textures
set pipeline broken FIX ME
[projectM] Allocating idle preset...
[PresetFactory] path is Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[PresetFactory] url is idle://Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[projectM] warning: no valid files found in preset directory ""
call factory clear here?
call factory clear here?
[projectM] config file: /home/adam/.projectM/config.inp
No Textures Loaded from /usr/local/share/projectM/textures
set pipeline broken FIX ME
Failed to insert builtin function "int" into collection! Bailing...
Aborted

```

---

### Post by sublimehypocrisy on 2009-05-05
Similar error: 

--------------------------------------------------------------------------------------------------------------------------------
paco@paco-desktop:~/projectm/projectM-Trunk/src$ projectM-pulseaudio
dir:/usr/share/projectM/config.inp 
reading ~/.projectM/config.inp 
[projectM] config file: /home/paco/.projectM/config.inp
No Textures Loaded from /usr/share/projectM/textures
set pipeline broken FIX ME
[projectM] Allocating idle preset...
[PresetFactory] path is Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[PresetFactory] url is idle://Geiss & Sperl - Feedback (projectM idle HDR mix).milk
[projectM] warning: no valid files found in preset directory ""
call factory clear here?
call factory clear here?
unconnected: connecting... 
connectHelper:  "alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.monitor" 
Segmentation fault
paco@paco-desktop:~/projectm/projectM-Trunk/src$ projectM-pulseaudio
--------------------------------------------------------------------------------------------------------------------------------

---

### Post by Grindolin on 2009-05-06
Hi together! 

I got the same error message with the segmentation fault.. Perhaps I figured it out.. (I figured it out for me.. ;) )

I tried to change the options in the ccmake configuration to get projectM work. 
When I switched the use of frame-buffer objects off (set USE_FBO to "off") it  finally worked.. :D 

Hope this will help also you to solve your prob with the segmantation fault.. 

greetz

---

### Post by BlairKatu on 2009-05-18
Thanks Grindolin your solution seems to work perfectly

> 
I tried to change the options in the ccmake configuration to get projectM work.
When I switched the use of frame-buffer objects off (set USE_FBO to "off") it finally worked.. 

---

### Post by Evil Wayz on 2009-06-02
> **Grindolin said:**
> Hi together! 

I got the same error message with the segmentation fault.. Perhaps I figured it out.. (I figured it out for me.. ;) )

I tried to change the options in the ccmake configuration to get projectM work. 
When I switched the use of frame-buffer objects off (set USE_FBO to "off") it  finally worked.. :D 

Hope this will help also you to solve your prob with the segmantation fault.. 

greetz


So the only way to make it work is compile it from source?  Then what's the point of having it in synaptic then?

I have this program working on one of my six computers.  I have no idea how I did it, and I can't duplicate it.  I started with the instructions here, and then I get the seg fault.

[http://www.ubuntu-unleashed.com/2008/04/howto-awesome-winamp-music.html](http://www.ubuntu-unleashed.com/2008/04/howto-awesome-winamp-music.html)

---

