---
title: "no sound from samsung  HDMI/DVI"
date: 2010-06-11
forum: Multimedia Software
---

### Post by hvc123 on 2010-06-11
morning all

i thought i would share my findings

i have a pc im using as htpc and plug the thing directly into my series 6 samsung (loads of hdmi ports)
im using a DVI - HDMI cable into hdmi/dvi port 3 which has a analogue audio port assigned to it.

after my initial install i had a fantastic picture but no sound.
after trawling the web for a while i could find no answer, infact i assumed it was ubuntus fault but i soon proved this otherwise with a pair of headphones.

anyway it seems that the Samsung series 6 dvi/hdmi (port 3) audio port is set to auto on the tv. meaning that if theres an audio feed coming down the hdmi cable it should switch to use that rather than the analogue port. so my problem is i have no audio from the analogue port.

i fixed this by going to the service menu of the samsung series 6 by pressing standby > info > menu > mute > standby on the control, this will turn the tv back on but with a blue screen and a service menu. i cant remeber where about the sound section is but when you find the hdmi/dvi section the sound is set to auto all i needed to do is set this to DVI and hey presto my sound now works.
DO NOT PLAY WITH THE SERVICE MENU TO MUCH AS YOU MAY BRICK YOU TV

---

### Post by alecao on 2012-04-28
> **hvc123 said:**
> morning all

i thought i would share my findings

i have a pc im using as htpc and plug the thing directly into my series 6 samsung (loads of hdmi ports)
im using a DVI - HDMI cable into hdmi/dvi port 3 which has a analogue audio port assigned to it.

after my initial install i had a fantastic picture but no sound.
after trawling the web for a while i could find no answer, infact i assumed it was ubuntus fault but i soon proved this otherwise with a pair of headphones.

anyway it seems that the Samsung series 6 dvi/hdmi (port 3) audio port is set to auto on the tv. meaning that if theres an audio feed coming down the hdmi cable it should switch to use that rather than the analogue port. so my problem is i have no audio from the analogue port.

i fixed this by going to the service menu of the samsung series 6 by pressing standby > info > menu > mute > standby on the control, this will turn the tv back on but with a blue screen and a service menu. i cant remeber where about the sound section is but when you find the hdmi/dvi section the sound is set to auto all i needed to do is set this to DVI and hey presto my sound now works.
DO NOT PLAY WITH THE SERVICE MENU TO MUCH AS YOU MAY BRICK YOU TV

Thanks! Worked for me!! The only difference is that my TV is samsung LCD 4 Series, the code for it's service mode is  Mute, 1, 8, 2, Power in sequence.

---

### Post by SL666 on 2013-01-03
THANKS! 

I had some issued trying to get HDMI sound - only seemed to work at 44100hz? (eg a video played that had that rate had sound - same type of video different rate didn't)

decided to drop back to analogue video - plugged in and no sound - your post helped me track down the solution.

service menu is the same config - Series 8 plasma.

I believe it was under config in the service menu - while trying to see if the service menu command was the same - I found plenty of people who had managed to change settings in there and now had less than functioning tvs - so be careful in there guys.

---

### Post by ddonov on 2013-06-13
No need to go to the service menu on newer Samsung TVs. All that needs to be done so that the TV starts using the DVI Audio In port is to set/change the name of the HDMI port to "DVI PC" (From the TV remote press Source->choose the so called HDMI/DVI port ->Tools->Edit name and from the list choose "DVI PC".
After this the TV will start using the DVI Audio IN port.

Let there be sound.

---

### Post by SL666 on 2013-06-14
> **ddonov said:**
> No need to go to the service menu on newer Samsung TVs. All that needs to be done so that the TV starts using the DVI Audio In port is to set/change the name of the HDMI port to "DVI PC" (From the TV remote press Source->choose the so called HDMI/DVI port ->Tools->Edit name and from the list choose "DVI PC".
After this the TV will start using the DVI Audio IN port.

Let there be sound.

That didn't work on my tv - and it's still the latest series i believe.

---

