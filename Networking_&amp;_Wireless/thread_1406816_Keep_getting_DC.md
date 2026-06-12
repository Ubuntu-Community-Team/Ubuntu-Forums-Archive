---
title: "Keep getting DC"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by Visello on 2010-02-14
First of all hello i am new to ubuntu and pretty much a big naab when it comes to this OS but trying my best :P

I have runnede ubuntu for alittel time now i and today when i did restart my computer i can't log on my net anymore it keep DC and retry log back to the net i have been reading alot on my damn iphone i finaly give up and go to the hardcore ubuntu peeps and ask for help 

I have been messing alittel around with firestarter to get vuze and my ps3 media server runing right but doubt it can be the firestarter since i tryede disable it and it says i can beforewlan0 is running

Cheers
/ Visello

---

### Post by Crafty Kisses on 2010-02-15
So I'm not sure I'm understanding your issue. The issue is you keep getting disconnected, but you can initially connect to the Internet? Here's what you can do to help me, help you out further. Go into the terminal **(Applications->Accessories->Terminal)** and run the following commands:
```
lspci
lsusb
lshw -C network
```
That will tell me a bit more about your network setup, and I don't think Firestarter would have anything to do with the issue, but to be sure you can always close it and see if the problem persists. I'd also like to see your kernel routing table, just to see what's going on, you can do this by running in the terminal:
```
route
```
So what you want to do is copy and paste all the results of all these commands here at the forum and remember to use the ***/code*** tags. I'm thinking this could very well be a module problem, but I don't want to jump to conclusions.

---

