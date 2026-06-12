---
title: "problems setting up Sony Handycam DCR-HC19E"
date: 2006-01-28
forum: Multimedia &amp; Video
---

### Post by blastradius on 2006-01-28
Hi

Just bought the above camcorder, I guess i should have checked compatability.  Anyway, how do I get Ubuntu Breezy to recognise it? and what's the best software package to use for home video level stuff?

Thanks

Eric

---

### Post by neocon2005 on 2006-03-21
I presume you want to transfer the video through IEEE1394/Firewire/iLink and convert to VCD/DVD. The best program I have found is Kino. Make sure you add your userid to the 'disk' group or set read/write(not sure if you need write?) permission to /dev/ieee1394 or /dev/raw1394. Search the forum on Kino issues if you have any; but the program is fairly self explainatory.
Enjoy!

---

### Post by Flapidouille on 2006-06-10
Hello, what happens if you do NOT have a firewire ? my Sony DCR-HC19E has only USB. Any solution ? do I just throw it away... ? Thanks to anyone with a suggestion.

---

### Post by blastradius on 2006-06-10
I'm now on Dapper but still no luck. I'm also trying to use USB.  Kino doesn't pick it up. I tried capturing my film to my Windows partition and reading it from there but Kino doesn't recognise the format.

---

### Post by el_baby on 2006-07-22
Did you see [thread=56468]this thread[/thread] about configuring a firewire connection for a Sony Handycam? USB seems to be non-workable... 

According to [Sony UK](http://www.sony.co.uk/), the [DCR-HC19E](http://www.sony.co.uk/view/ShowProduct.action?product=DCR-HC19E&pageType=TechnicalSpecs) **does have** a firewire port... it seems to be *output only*... it should be labeled **[color=blue]i.Link[/color]** or **[color=red]DV[/color]**. It doesn't seem to include the firewire cable so you'd probably have to get that (and the card, too, if it's not included in your computer).

I just got a new [DCR-HC36](http://www.sonystyle.com/is-bin/INTERSHOP.enfinity/eCS/Store/en/-/USD/SY_DisplayProductInformation-Start?ProductSKU=DCRHC36)... it has a firewire port (labeled **[color=red]DV[/color]**), but no firewire cable, only USB... I'm about to borrow a firewire card and cable from a friend to test it...

---

### Post by Flapidouille on 2006-07-24
Well,at least one does not feel alone...Perhaps some day somebody will come with good news,a solution, that is.. The main -and only- problem is that everything we buy is formatted to be W$-dependant. When linux is widely accepted, then everything will be working. Better !
Thanks for your answer anyway.

---

### Post by el_baby on 2006-07-24
Yeah, I know... anyway, Sony (and most device providers) has this tendency to include less and less options with their gadgets... that is, about a year ago, all handycams that had a firewire port, came with a firewire cable... now you have to get it by yourself... about 6 moths ago, most middle range handycams had composite video input/output ports... now only the top of the line have that, and the middle range have only output ports...

---

