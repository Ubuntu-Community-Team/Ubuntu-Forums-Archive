---
title: "f-spot extensions will not install"
date: 2009-04-25
forum: Multimedia Software
---

### Post by geoffDeGeoffGeoff on 2009-04-25
I have tried to install the picturetile and metapixel extensions using the edit >> manage extensions >> install extensions  on intrepid

The new functions appear in the Tools menu but attempting to use them gives variations of the following:
The picturetile.pl executable was not found in path.  Please check that you have installed it and you have permissions to execute it"

---

### Post by chrisbay90 on 2009-05-31
> **geoffDeGeoffGeoff said:**
> I have tried to install the picturetile and metapixel extensions using the edit >> manage extensions >> install extensions  on intrepid

The new functions appear in the Tools menu but attempting to use them gives variations of the following:
The picturetile.pl executable was not found in path.  Please check that you have installed it and you have permissions to execute it"

I am having the same problems (Only difference is im using Ubuntu 9.04)

Could anyone please help?

---

### Post by catchmeifyoutry on 2009-12-06
According to the F-Spot website (see [Extensions page]("http://f-spot.org/Extensions#PictureTile_integration_for_photowall_generation")), you need [PictureTile]("http://www.jwz.org/picturetile/") installed.

I didn't find PictureTile in the ubuntu repositories, but it's just a simple perl script.
For me it worked to just download the script and place it in your home's ~/bin/ directory.

In the terminal:
[PHP]
cd ~/bin
wget http://www.jwz.org/picturetile/picturetile.pl
chmod +x picturetile.pl
[/PHP]

Hope this helps ;)


Note that picturetile requires ImageMagick to be installed, which is in the ubuntu repositories:
[PHP]
sudo aptitude install imagemagick
[/PHP]

---

