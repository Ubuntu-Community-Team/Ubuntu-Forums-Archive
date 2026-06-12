---
title: "PACPL Pearl Audio Converter help!!"
date: 2011-01-30
forum: Multimedia Software
---

### Post by ajpearson on 2011-01-30
I have installed this program ok but I am new to command lines in terminal.

I want to convert some wav files to wma files. I have the wav files currently in a folder called Test to make it easy. So I have entered the following command line:

ajpearson@ajpearson-laptop:~/Desktop/pacpl-4.0.5$ pacpl --to wma home/ajpearson/Desktop/Test

and the error message I get is:

error: the following is not a file or directory: home/ajpearson/Desktop/Test


It does not matter what directory I use I get the same error. I am sure the answer is obvious - but not t me. Any help will be greatly appreciated.

Thanks
Andrew

---

### Post by gordintoronto on 2011-01-30
I think you need to specify /home/ajpearson/Desktop/Test

Without the leading slash, Linux looks in the current folder, for a folder called home.

However, I also suggest you run Administration/Synaptic Package Manager, and search for soundconverter and then you won't need to use the command line.

---

### Post by ajpearson on 2011-01-30
Many thanks for replying. So does soundconverter link to this Perl Audio somehow - sorry but so ignorant of all this?

Thanks Andrew

---

### Post by gordintoronto on 2011-01-30
I have never heard of Pearl Audio before. Soundconverter is a front-end for some command-line tool. It works very well.

---

### Post by ajpearson on 2011-02-01
I like the look and feel of soundkonverter - it certainly gives the option for WMA. However when I convert the WAV files to WMA it seems to work and creates WMA files. Nothing in Ubuntu or Windows recognises the WMA files - they do not play.

Is there something further I need to do with the soundkonverter settings to ensure it creates a WMA file ok? Do I need to load some further plugins.

Thanks

Andrew

---

### Post by gordintoronto on 2011-02-01
I actually suggested a program called soundconverter, I'm not sure if that is what you installed. You might need to do this:

"Go to Administration/Software Sources and enable the Medibuntu repository. Close that and run Administration/Synaptic Package Manager. Click on "reload," then install the "non-free codecs"."

---

### Post by ajpearson on 2011-02-02
Thanks for all your help.

I already had soundconverter (there is another program called soundkonverter). But soundconverter never had the option for WMA - so I presume this is the non free codecs you mention.

I could not find the Medibuntu repository in Software Sources. I also could not find the Non-Free codecs in synaptic but presume I need Medibuntu first.

However, now for some reason when I rip wav tracks from soundconverter all I here is static when I play back.

I appreciate all your guidance and help - I feel completely lost. At the moment, my sound in ubuntu is awful, my printer does not link up and work, my external dvd writer. Ubuntu seemed to get worse when I upgraded to the current version. I feel like packing it in and starting again.

Andrew

---

### Post by gordintoronto on 2011-02-03
In my Software Sources, I click on the "other software" tab and Medibuntu is the fifth item on the list. I only enabled it quite recently. I am using Ubuntu 10.10. Medibuntu has been around for several years.

What printer? For my network Brother laser, I started Administration/Printing, clicked on "add" and said it was a network printer. After a few seconds, Ubuntu found it, and a couple of very obvious clicks later it was working.

I have no suggestions about an external DVD writer.

---

### Post by Chronon on 2011-02-03
> **gordintoronto said:**
> I have never heard of Pearl Audio before. 
It's actually called Perl Audio Converter.

---

### Post by ajpearson on 2011-02-06
To gordintoronto
Thanks for all you help and support.

I am embarrassed to admit that my "new download" icon had disappeared and when I looked at download manager I was not on the recent Ubuntu version - so I have now upgraded and many of my problems have disappeared. The sound is superb, the external dvd writer works, the audio files play and Soundkonverter converts to WMA ok. I will look at how I update soundconverter to do the same.

My only problem is the print  Canon MP240, but there appear to be a few threads that support this printer so I will investigate and start a new thread.

I just wanted to thank you for your help and patience - I am sure there is a way of thanking you in the system but will have to find out how - "learning all the time"

I would be lost without forum help!

---

