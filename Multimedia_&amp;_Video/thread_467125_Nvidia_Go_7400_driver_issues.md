---
title: "Nvidia Go 7400 driver issues"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by Arasa on 2007-06-07
I am a complete newb, and I just installed feisty fawn. Been reading forums here and there.

Everything went well, except it refused to use the nvidia-glx or nividia-glx-new drivers, after installing either, upon restart, it gives me a message that an error has occured, some messed up text, I click details but nothing clear for me to pick out, I go back to xorg.conf and revert to default nv driver, then its possible to use gui again.

I read another post and there followed the steps, similar to before, but it included a switch "-no --composite" (not sure if I quoted that right, but you get my point.)

I restarted and all is well, I can see it has detected my card and the gui starts fine, problem is now, I can't use any background effects etc because composites have been disabled.. 

So the issue, is not getting the driver to install, it's getting it to work

Has anyone had any similar problems and any possible ideas/solutions.

Help much appreciated, 




Arasa

---

### Post by straps on 2007-06-07
Hi have an HP dv6000 with a NVidia GeForce GO 7400 and it works well

Feisty has installed NVidia restricted drivers automatically through **System->Administration->Restricted Driver Manager** or launching **sudo restricted-manager**

I have attached my xorg.conf

Bye

---

### Post by Arasa on 2007-06-07
Thanks,

I also have hp dv6000 series.

I couldn't get the config you posted to work -don't worry I didn't copy it word for word, from what I understand, it is set up to run 2 monitors. Also, not sure about the line containing stuff about the bus. 

But I did manage to find a way in the end, so I have fully installed and can run the latest nvidia driver with composite enabled, thus I now have some basic desktop effects.

Next step is a little more customization maybe even beryl if I have the courage;)

Here is the link:

[http://frenchninja.wordpress.com/2007/01/06/how-to-install-berylaiglx-on-debian-etch/](http://frenchninja.wordpress.com/2007/01/06/how-to-install-berylaiglx-on-debian-etch/)

Thanks again,



Arasa

---

### Post by straps on 2007-06-08
Try here
[http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28Nvidia.29)

---

