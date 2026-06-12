---
title: "How to config my refresh rate LG F900P?"
date: 2005-11-13
forum: Multimedia &amp; Video
---

### Post by syrex2 on 2005-11-13
Hello all :)
How to config my refresh rate with LG F900P & Geforce 6600GT
In prefences I can choose only 60mht...

I've read the faq,but it just confuse me more,I don't want to harm my monitor 
so I'm asking your help...

Thanks ubuntu is gr8 :P

---

### Post by Teroedni on 2005-11-13
here is link to supported mode
[http://www.ciao.co.uk/Productinformation/LG_Flatron_F900P__5393906/](http://www.ciao.co.uk/Productinformation/LG_Flatron_F900P__5393906/)


just look over it and teel us what you want
we will have to edit a little but its not dangerous;)

---

### Post by syrex2 on 2005-11-13
First of all thanks.

this is the command right?

sudo dpkg-reconfigure xserver-xorg

---

### Post by syrex2 on 2005-11-13
Enter your monitor's horizontal sync range.   (default 28-51)
Enter your monitor's vertical refresh range.    (default 43-60)  
                         &#9474;

and the depth color I chose 16.

Thanks.

---

### Post by Teroedni on 2005-11-13
So it works now?

---

### Post by syrex2 on 2005-11-13
[QUOTE=Teroedni]So it works now?[/QUOTE]


This is my default (what ubuntu chose for me-not working well) ,i'm asking what to fill in them.

thanks,and sorry about the misunderstanding.

---

### Post by Teroedni on 2005-11-13
[QUOTE=syrex2]This is my default (what ubuntu chose for me-not working well) ,i'm asking what to fill in them.

thanks,and sorry about the misunderstanding.[/QUOTE]


Max Sync Rate (V x H)  	200 Hz x 107 kHz

Horinzontal max 107 kHz
Vertical max 200hz 


also
Enter your monitor's horizontal sync range. (default 28-107)
Enter your monitor's vertical refresh range. (default 43-200)

---

### Post by syrex2 on 2005-11-13
Thank u I'll try it.

---

