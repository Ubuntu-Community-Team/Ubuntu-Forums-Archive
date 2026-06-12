---
title: "minicom - how to send AT commands to programmable LCD"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by oliversk on 2010-12-19
Hi everyone, 

I am new to Ubuntu and I love it. I am trying to send some commands to a **programmable LCD displayvia minicom**. 

I can connect now without problems, but I don't have a clue how to send the commands. 

**Examples of commands**
> System commands

#**@Reboot**[COLOR="Red"] ==> how to enter this in minicom[/COLOR]
Restarts the LCD

#@EnterISP
Restarts the LCD and enters the programming mode for 2 minutes. The LCD will restart automatically 
after 2 minutes. Use FlashMagic ([http://www.flashmagictool.com/](http://www.flashmagictool.com/)) to upload new firmware to the LCD 
over the same serial link.

#@Display On
#@Display Off
Turns the display on/off
[COLOR="Blue"][Source]("http://www.omnima.co.uk/forums/index.php?showtopic=118")[/COLOR]

So, now what do I have to enter to make it work? I'm sorry I wouldn't even know how to enter the @ sign. In hyperterminal on Windows I can connect just fine and when I enter AT it gives me an "OK", but in minicom I don't have a clue what to do. Well, I assume that I need to enter it in **hex or ascii code and that i need to add CR/LF at the end** .. but that did not really work for me 

I would appreciate any tips how to use minicom...

Thanks,
Oliver

P.S. Happy Holidays

---

### Post by oliversk on 2010-12-19
Tried entering something like


[LIST=1]
[*]64 826966797984 for AT Reboot
[/LIST]

---

### Post by oliversk on 2010-12-19
Ok, so when I enter 
AT 826966797984 

and then exit minicom I get some new text on the screen like AT S7=45 S0=0 L1A 

I added a "line feed", does that mean it automatically adds the CR/LF at the end? I'm pretty confused..

---

