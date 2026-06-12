---
title: "[SOLVED] How to convert a still image into a movie?"
date: 2007-10-11
forum: Multimedia &amp; Video
---

### Post by berliita on 2007-10-11
I've got in my hard-drive a still image of myself, which i'd like to upload to YouTube, so i can use it as my channel's thumbnail. As far as i know, YouTube requires that all uploaded files be movies; still images can't be uploaded. I haven't a video camera, so i'd like to convert my still image to a movie. I've actually managed to accomplish this using Cinelerra. But it seems overkill. Is there any simple way to do it, say using just the command line?

---

### Post by leonidas666 on 2007-10-11
i'm no youtube expert, but it seems a bit strange to me that a channel thumbnail should be a video. Maybe you can find a better way to create that thumbnail than using a video.

Anyway, i'm using KDE, and i have KIM installed. Kim is basically a gui for imagemagick in konqueror. In the KIM menu there's also a option to create a mpeg movie out of a list of  pictures. So if you want to do it from the commandline, probably imagemagick can do it. 
For the exact details you'll have to dig yourself through the page-long documentation of imagemagick  ... or you use KIM ;-)

---

### Post by berliita on 2007-10-11
Thanks, leonidas666. I've installed KIM (or, rather, konq-kim, which, i believe, is what you were referring to; in any case, there isn't any plain "kim" on my Synaptic list). But i see no special kim menu in Konqueror. The closest option is Location->Open with Image Viewer, but i see no option to create an mpeg movie out of a list of pictures there.

---

### Post by leonidas666 on 2007-10-11
Yes, i guess in synaptic it's called konq-kim.

As far as i remember i did not do anything extra, i just installed the package and then i had that context menu. When i right-click in konqueror on a .jpg image, the context menu has a entry "actions", and after this entry there are all the things kim can do with the image. 
Maybe there is something wrong with your kde/konqueror installation?

---

### Post by Masterj15 on 2007-10-11
> **berliita said:**
> I've got in my hard-drive a still image of myself, which i'd like to upload to YouTube, so i can use it as my channel's thumbnail. As far as i know, YouTube requires that all uploaded files be movies; still images can't be uploaded. I haven't a video camera, so i'd like to convert my still image to a movie. I've actually managed to accomplish this using Cinelerra. But it seems overkill. Is there any simple way to do it, say using just the command line?

if where talking about any os then try sony vegas. Just pop your picture in their and save as a mp4 or something. Thats what I did and it turned out flawless!

---

### Post by berliita on 2007-10-11
Oh, a CONTEXT menu. Sure, now i see it: Actions->Kim - PlugIns->Make a Mpeg movie. But when i try to use it, i get the error message: "Could not find the program 'images2mpg'". Unfortunately, a Synaptic search for a package name or description containing the string "images2mpg" yields no result. Anyone knows where this program is to be found?

---

### Post by nzadLithium on 2007-10-11
ffmpeg can do it using the command line

this is the command you want:

replace %03d with watever your image is called
im not sure what other types of images ffmpeg supports but i'd say try it and see if it works if your image isnt a jpeg. (otherwise you could just use the gimp and resave it)

and replace file with watever you want the movie to be called

ffmpeg -i %03d.jpg file.mpg

ffmpeg is in synaptic

---

### Post by berliita on 2007-10-12
Thanks, nzadLithium. I've tried your suggestion. I didn't have to download ffmpeg specifically for the occasion, since i've been using it successfully for some time to convert between different movie formats. Unfortunately, the .jpg to .mpg conversion didn't go well. I applied the procedure twice to a couple of .jpg pictures. On the first attempt, the following error message displayed: "pic1.jpg: Unknown format". On the second attempt, the following error message displayed: "pic2.jpg: could not find codec parameters". Both pictures open smoothly in Gimp.

---

### Post by nzadLithium on 2007-10-12
what are your pictures called?

what was your complete command?

---

### Post by berliita on 2007-10-12
My pictures are called - hold on tight - "pic1.jpg" and "pic2.jpg". These are no placeholders for the actual names. These ARE the actual names. The commands i used - again, brace yourself - are:
```

$ ffmpeg -i pic1.jpg mov1.jpg
...
pic1.jpg: Unknown format
$ ffmpeg -i pic2.jpg mov2.jpg
...
pic2.jpg: could not find codec parameters

```

---

### Post by eye208 on 2007-10-12
Here's how to do it:

Use two copies of the same picture. Name them pic1.jpg and pic2.jpg. Then enter the following:

mencoder "mf://pic*.jpg" -mf fps=0.1 -ovc x264 -o movie.avi

The reason why we are using two frames here is because movie players will treat 1-frame movies different. A 1-frame movie in mplayer will have zero duration, i.e. the player window will close immediately. Since we don't know how Youtube will treat them while transcoding to Flash video format, it's better to use at least 2 frames just to be on the safe side.

---

### Post by timcredible on 2007-10-12
digikam will easily convert a picture (or multiple pictures) to a video with or without sound (it's their slideshow option in Tools).  digikam is in synaptic, just add it, point it to where your picture is, a couple of mouse clicks, and you're done.

---

### Post by berliita on 2007-10-12
eye208 and timcredible, thank you both for your replies.

eye208, your solution's worked like a charm. In fact, i was able to get by without the "mf" option, thus:
```

$ mencoder "mf://pic1.jpg" -ovc x264 -o movie.avi

```
Could you tell me, please, what the "mf://" prefix is there for? I tried to do without it, but it didn't work. What does "mf" stand for?

timcredible, i've installed digiKam, created a new album, imported my pictures to that album, selected them, and then opened the "Tools" menu. There was no "Slideshow" option there. There was, however, a "Slideshow" submenu in the "View" menu. So i clicked View->Slideshow->Selection. That played a full-screen slideshow of the pictures. Great, but not quite what i have in mind. I would like to capture this sideshow in a movie file, to be posted on such sites as YouTube.

---

### Post by nzadLithium on 2007-10-12
its because you've told it to decode  a jpeg and encode a jpeg. use mov.avi or mov.mpg

---

### Post by berliita on 2007-10-12
nzadLithium, i made a typo earlier, sorry. The code i actually typed in was:
```

$ ffmpeg -i pic1.jpg mov1.mpg
$ ffmpeg -i pic2.jpg mov2.mpg

```
I've tried to do the same with "mpg" replaced by "avi", and the results were exactly the same.

---

### Post by nzadLithium on 2007-10-13
i found out whats wrong. You cant do just one jpeg by itself. duno why. but you can put ffmpeg -i pic%03d.jpg mymov.mpg

and as long as you start numbering at 0 it will work fine. You would probably want to play with the frame rate though im pretty sure frame rate is specified by -r

I had problems with mencoder. I got the latest version off the mplayer website and all of the manuals in ubuntu and on the net are too old and don't have info about its current syntax :S

---

### Post by berliita on 2007-10-13
The application "images2mpg" is part of the package "kipi-plugins", available via Synaptic. This program can be run from the command line, as follows. To convert an image, "pic.jpg", into a movie, "mov.mpg", of duration 3 seconds (25 fps, dimensions: 720x576), enter the following command:
```

$ images2mpg -d 3 -o mov.mpg -i pic.jpg

```
The number of frames per seconds as well as the dimensions of the resulting movie can be controlled only to a rather limited extent. See the excellent man page for further details.

Thanks, leonidas666, for informing me of this application. Thanks all the other users, as well, particularly eye208. Each of you has contributed valuable information to this thread. :)

---

