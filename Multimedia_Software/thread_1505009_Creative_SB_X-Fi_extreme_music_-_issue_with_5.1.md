---
title: "Creative SB X-Fi extreme music - issue with 5.1"
date: 2010-06-08
forum: Multimedia Software
---

### Post by E_is_for_Eric on 2010-06-08
So here is my conundrum. I installed Ubuntu 10.04 last night and was listening to music with my headphones so as to not disturb anyone else in the house. (It was late.)

I did check to see if my 5.1 surround system would work with Ubuntu, but I only get the front two channels (L/R) and my Subwoofer.

So here is what I have done: I have run my update manager several times to make sure I have those updates installed, and checked the Hardware Drivers function to see if my soundcard needed anything selected there (and it didn't).


When I go to Sound Preferences and select the Hardware Tab and choose my device to configure 'SB X-Fi 1 Output/1 Input' - I go to the bottom of the window and choose profile.

If I choose anything other than 'Analog Stereo Output' the audio quality is flat, and often has feedback and distortion. When I choose Analog Stereo Output, I only get the two front channels and subwoofer. However, if I select 'Analog Surround 7.1 Output' then I will get my two rear channels along with my two front channels and subwoofer. I would be fine running with the 7.1 profile, but, I don't get my center channel.

I've done some quick research at several different places and it seems the best way for me to solve my issue is to download the ALSA drivers. The problem I run into now is, I'm very new to Ubuntu and I'm not yet familiar and comfortable with the terminal/command line system yet. So if the download does not have a built in unpacking unit I get very confused quickly.

I realize that this is starting to become a big post and I could keep going, but I think I should stop here and wait for a response and then once someone who knows what they are doing starts talking to me, I can give any more or direct information as needed.

Thanks in advance.

*edit*
I did a quick forum search with the keywords X-Fi and a few variations and didn't see any results. I sincerely apologize if this is a double post or if there is a solution posted somewhere in the forums; and if there is, a link to that thread would be most appreciated.

---

### Post by E_is_for_Eric on 2010-06-08
I solved my problem by running the ```
alsamixer
``` command in terminal.

---

### Post by ktechman on 2011-05-04
With the above mentioned card SB X-FI on a Dell Dimension E520 I disabled the on-board sound and the audio card functioned as expected with mic and speaker working normally. Solved

Ktechman

---

