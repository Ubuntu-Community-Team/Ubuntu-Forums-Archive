---
title: "Covert video to mp4 for iphone 4?"
date: 2011-03-11
forum: Multimedia Software
---

### Post by numbness05 on 2011-03-11
I wonder if any body is able to assist me.

I have just received my iphone 4 16gb, I had already looked into a work around for the whole itunes inside linux issue and instead opted for gtkpod ipod manager which works a treat for my music however I have no way of converting and putting movies on my phone.

Previously I would have used Handbrake to do my video conversions however the new version download on their site doesnt work with 10.10 for some reason and both handbrake and gtk gui are missing when I look in the ubuntu software updates....

Any bright ideas any one I'm completely lost after 12 hours of searching.

Many thanks

---

### Post by shantiq on 2011-03-12
ok numb one i suggest try to install it again     works fine on my 10.10 and handbrake definitely the best for what you want

in your terminal write:

```
sudo add-apt-repository ppa:stebbins/handbrake-releases
```

```
sudo apt-get update
```

```
sudo apt-get install handbrake
```




and **then ** go to synaptic and make sure gtk is clicked in see image


should all work:KS

---

### Post by numbness05 on 2011-03-14
Thanks for that tried all of the above and it still fails to open. 

Any other suggestions at all please?

---

### Post by shantiq on 2011-03-15
have you looked at winff which is the gui for ffmpeg   it might do what you want


```
sudo apt-get install winff

```


do not understand why your handbrake does not start     does it appear in your synaptic at least now as in attached image above?

================================

ok if it appears in your synaptic **here is probably** the answer

run  ```
ghb
```   in your terminal

who could ever guess that???


other route is Alt+F2 and write the same  ```
ghb
``` scroll down the list find handbrake and see the code is ghb


Fingers crossed:KS

---

### Post by numbness05 on 2011-03-15
Hey man thanks for that.

Yes it does appear in synaptic and in ubuntu software centre but would not open, but for what ever reason running ghb in terminal has... huh go figure?

Well at least it does open all I need to do now is find a way of getting converted videos onto my iphone 4, as itunes is refusing to copy over any films or film clips even when converted they simply refuse to add them selves to my library.

I don't suppose you know of any linux native software that is capable of this do you?

Once again thank you for your help.:D

---

### Post by shantiq on 2011-03-15
ok numb good news there


1.   i suggest now you have a launcher on your desktop for handbrake with ghb command

right click on desktop then create launcher and enter ghb
and that is sorted


2.As regards the transfer i think that probably [this looks like a good place to start]("http://www.gtkpod.org/wiki/Home")

```
sudo apt-get install gtk-pod
```   it says it does video too but i have no ipod myself and therefore no experience

**But** your best bet is probably ** banshee** which is highly rated and will be the default player in Natty Narwhal


```
sudo apt-get install banshee

```


if you check the attached image many leads there


tell us how you get on     no doubt someone else will see this post who has an ipod and point you in the right direction:KS  but you may find banshee and gtk-pod do the business

---

### Post by numbness05 on 2011-03-15
Excellent I seem to be making progress all be it in a different direction.

I have a video converted using handbrake but I was unable to put the video onto my iphone using gtkpod ipod manager (kept displaying "Unsupported checksum type") 

I eventually gave in with that and went back to itunes on my windows machine (sorry had to be done for these purposes bloody Apple not supporting Linux) I removed the version I had and reinstalled it. I am now able to add the video I converted into my itunes library and am now just waiting until the end of the earth for it to finishing syncing.... its being going for an hour now.

Think I will look into Amarok tomorrow though.

Many thanks again buddy!

Will report back on Amarok

---

