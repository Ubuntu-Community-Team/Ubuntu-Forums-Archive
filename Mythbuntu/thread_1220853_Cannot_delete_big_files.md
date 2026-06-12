---
title: "Cannot delete big files"
date: 2009-07-23
forum: Mythbuntu
---

### Post by chipppy on 2009-07-23
**[SOLVED with thanks for the assistance]**

Good Evening

I am trying to delete a file that is 5.2GB. 

I right click on the file in Thunar and then select delete.  
The file starts to delete and after some time the bar has moved along to about 70-80% moving to garbage.  Then a message comes up saying that there is not enough room in the garbage bin for the file.  

I have emptied the garbage bin and it is empty and tried again and still not enough room.

It seems that this file is just to big.  I have tried a few different methods to delete this file but always run into the not enough room problem.

Anyone know how to increase the size of the garbage bin in XFCE desktop or how to delete big file?

Thanks for any and all assistance.

cheers
chipppy

---

### Post by klc5555 on 2009-07-23
> **chipppy said:**
> Good Evening

I am trying to delete a file that is 5.2GB. 

I right click on the file in Thunar and then select delete.  
The file starts to delete and after some time the bar has moved along to about 70-80% moving to garbage.  Then a message comes up saying that there is not enough room in the garbage bin for the file.  

I have emptied the garbage bin and it is empty and tried again and still not enough room.

It seems that this file is just to big.  I have tried a few different methods to delete this file but always run into the not enough room problem.

Anyone know how to increase the size of the garbage bin in XFCE desktop or how to delete big file?

Thanks for any and all assistance.

cheers
chipppy

Just open a terminal and use the "rm" command. 

rm /[path-to-file]/[filename]

Type accurately: the file is not recoverable after it's been removed with rm.

In general, I don't like graphical interface file managers. Even though Thunar is better than most, I still find it cumbersome and flakey. So, without exception the first thing I do on a Ubuntu install of any sort is to install the old text-mode file manager Midnight Commander ("mc") --("sudo apt-get install mc"). And then I run it from a terminal whenever I need to do serious file management chores, or with "sudo" whenever I need to do the same with root privileges or need a convenient command shell with root privileges. I'd hate having to get by without it.

---

### Post by SiHa on 2009-07-23
..or if you're not comfortable with a terminal, I think you can use Shift + Del, like in Windows to permanently delete a file, rather than move it to the recycle bin.

---

### Post by chipppy on 2009-07-27
Good Afternoon

The shift delete worked great. 
I also tried the rm [filename] after navigating into the required folder.  This works as well but I am more comfortable with the Thunar way.  I suppose it just a hangup from those old windoze days.

All is good.  Thanks heaps for the assistance

cheers
chipppy

---

