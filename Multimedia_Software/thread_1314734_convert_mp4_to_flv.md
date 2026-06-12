---
title: "convert mp4 to flv"
date: 2009-11-04
forum: Multimedia Software
---

### Post by fcuk112 on 2009-11-04
any tool in ubuntu to convert mp4 files to flv?

i read that you can do it with ffmpeg, but not sure what params to pass.  could someone please provide a working example?

thanks!

---

### Post by stinger30au on 2009-11-04
handbrake will do it easy

[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by FakeOutdoorsman on 2009-11-04
> **fcuk112 said:**
> any tool in ubuntu to convert mp4 files to flv?

i read that you can do it with ffmpeg, but not sure what params to pass.  could someone please provide a working example?

thanks!

Show the output of:
```
ffmpeg -i your_input_file_that_you_want_to_convert_to_flv.mp4
```
This will give useful info about the input file so it will be easier to come up with a FFmpeg command.  Also, why flv?

---

### Post by fcuk112 on 2009-11-05
thanks for the feedback.  i looked at the handbrake website and it seems it's not available for ubuntu at the moment.  tried the windows version, but unfortunately it doesn't have any output option for flv files.

i will try your ffmpeg suggestion.

i am using flv files because i need to integrate the files with a flash video carousel.

cheers, frank.

---

### Post by pogo07 on 2010-09-24
> **FakeOutdoorsman said:**
> Show the output of:
```
ffmpeg -i your_input_file_that_you_want_to_convert_to_flv.mp4
```
This will give useful info about the input file so it will be easier to come up with a FFmpeg command.  Also, why flv?

The actual format for the ffmpefg command is:  
ffmpeg -i [flv file name you want to convert].flv [new mp4 name].mp4
Note the space between the file names.  The easiest way to do this is to put the flv file on your desktop.  Open terminal and change to the desktop [cd ~/Desktop].  Then run the above command in terminal.

---

