---
title: "Very poor picture from svideo out"
date: 2009-11-10
forum: Mythbuntu
---

### Post by idrisdraig on 2009-11-10
(Please bear in mind I know nothing about either using Linux or doing _**ANYTHING**_ without a GUI.)

I have just installed 9.10.
As part of the process I was asked about settings for my graphics card.
It is an Nvidea G-Force 6200 card and since I want to connect to a CRT TV with only SCART inputs, I am using the s-video output and an s-video to scart cable.
IIRC there was a point where I chose Nvidea (there was one other option but I can't remember what it was) and a point where I think I had tro drop down lists that had something to do with selecting the S-video output.
Whenever the TV standard was asked about I selected PAL or PAL-I (I'm in the UK.)

The VGA output seems to have nothing output from it and the s-video output is very very poor quality - it is colour, but the picture bleads heavily and when looking at xfce (I think that's the GUI, right?) the text is bearly legible.

Any suggestions on how I might be able to improve this?

---

### Post by gwagchunks on 2009-11-10
I'd hate to say it but a new TV might be in order. Seriously, I have tried my machine with s-video from the graphics card to the s-video input on my CRT TV, and while it's better than my VCR for normal TV, the desktop gui (linux or windows) desktop is very fuzzy, and in myth, most of the menus are not quite the right size on the screen and keep going off the edge of the display. It is much much better with VGA on my LCD TV with VGA input. I'm saving up for a new TV! :D

To get VGA working again, I think from memory there is a option (twinview) that outputs both to the s-video and VGA. You can get to it from the gui (when you exit out of myth) there is an option for nvidia control panel?

---

### Post by idrisdraig on 2009-11-11
Any ideas why the svideo isn't working?

---

### Post by SiHa on 2009-11-11
S-Video is simply a very poor standard. It's one step up from composite, but only just. For watching video it might be just about acceptable, but for something with nice sharp edges and high contrast ratios (white text on a black background) it'll just be pants.
My first Myth setup used S-Video, and the picture wasn't good. I did however manage to improve it considerably by purchasing a quality cable. Most cheap S-Video cables are not made with coaxial cable, and therefore aren't 75ohm. It improved my picture enough that I used it for a few months before we came into a bit of cash and upgraded to an LCD.

---

### Post by pootle1 on 2009-11-11
That sounds like s-video to me, when I first started using tv's I found I had to limit the screen resolution to 640 X 480 for text to be readable over an s-video connection, you might get a slight improvement with a better cable, but if it already a short cable, then it probably won't make much difference.

---

### Post by idrisdraig on 2009-11-11
The cable is only 1.5m, and the TV picture is almost as bad as the desktop. ie not really useable.

Is there any viable (cheap) way to use a CRT? (FWIW My gfx card has DVI and VGA, but the TV has neither - just SCART and RF.)

---

### Post by SiHa on 2009-11-11
Have you tried playing with the settings in the Nvidia-Settings app. Either run```
sudo nvidia-settings
``` in a terminal or select Nvidia X-Server Configuration (IIRC) from the System menu.
I think there's a few settings like phase etc, that you can twiddle with.

---

### Post by mythding on 2009-11-11
I am ashamed to admit it but my bedroom 32' HDTV is getting picture from an s-video cable until I get a new HDMI cable. The picture looks pretty decent from my bed (not from up close, very pixelly). I have a good quality cable and had to massage the hell out of the nvidia settings and the tv picture settings but I have not had any complaints from the wife. But I can definitely see the desktop text and read most web pages.

---

### Post by idrisdraig on 2009-11-11
Presumably if it's an HDTV it's not a CRT. (Don't know how relavent the answer is but still ...)
What massaging did you find made a difference?

---

### Post by kio_http on 2009-11-11
Simple svideo tends to get a lot of interference. Try connecting with VGa or HDMI/DVI

---

### Post by mythding on 2009-11-11
> **idrisdraig said:**
> Presumably if it's an HDTV it's not a CRT. (Don't know how relavent the answer is but still ...)
What massaging did you find made a difference?

I dont really know. I adjusted the tv with the highest contrast possible and adjusted the colors to my liking. Then I opened up the NVidia settings and started screwing around with all the settings till I got something that looked decent. I am not home right now but if you want, when I get home I can post the exact settings I currently have.

---

### Post by idrisdraig on 2009-11-11
**kio_http** As stated, the TV just has SCART and RF input.

** mythding** thanks - doubtless the settings will be different for my TV but it would be interesting to see what sort of changes might work

---

### Post by nickrout on 2009-11-11
The best output from s-video into a TV is usually at a native tv resolution - thats 720x576 for PAL and 720x480 for NTSC. 

I am pretty sure the nvidia drivers have mode names that correspond to those resolutions.

---

### Post by idrisdraig on 2009-11-12
> **nickrout said:**
> ... nvidia drivers have mode names that correspond to those resolutions.Sorry, you've completely lost me there.

---

### Post by gwagchunks on 2009-11-12
I have an old desktop with a nvidia card which I think is similar to yours (and an 32" CRT TV). I'll load up mythbuntu 9.10 on it (might be next week now though) and make a note of settings and see what the quality is like and report back.

---

### Post by idrisdraig on 2009-11-12
Thanks.

---

### Post by nickrout on 2009-11-12
run nvidia-settings.

click on 'x server display configuration'

in the 'resolution' drop down menu choose '720x576'

click 'apply'

---

