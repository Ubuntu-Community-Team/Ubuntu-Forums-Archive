---
title: "Xerox 3025Bi will not print"
date: 2024-12-05
forum: MINT
---

### Post by sulani on 2024-12-05
[COLOR=#333333][FONT=&amp]Hi[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]I got a xerox workcenter 3025BI.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]I have linux mint 22 cinnamon on my laptop. The laptop is an Asus Vivobook. I connected the printer via USB cable. The printer will print a test page no problem.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]The printer gets recognized but when I send something to print the display on the printer just says printing for a second and disapears, it does not print.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]I downloaded the linux driver from the xerox website but I have no idea how to install it. I also disabled IPP[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]I extracted the files in the driver.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]When I click on the install.sh installprinter.sh isntallscaner.sh files it ask me to choose run in terminal, display, cancel and run.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]When I click run in terminal the terminal flashes for a second and goes away.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]The printer description and the box clearly stated it is linux compatible.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]I threw the box away so I cant return it I am stuck with this thing.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]Can you help me.[/FONT][/COLOR]

---

### Post by coffeecat on 2024-12-05
Hello sulani, this forum is shortly to close down with support for Ubuntu and the official Ubuntu flavours moving to Ubuntu Discourse. A few points.

[list=1]Mint is not an Ubuntu flavour, so I've moved your post to our Mint sub-forum.
[*]Please do not post to Ubuntu Discourse. Although based on Ubuntu, Linux Mint is not Ubuntu, and I believe that Ubuntu Discourse will close threads about Mint as being off-topic.
[*]The best place for Linux Mint questions is on their own forum here: [https://forums.linuxmint.com/](https://forums.linuxmint.com/)
[/list]

---

### Post by yancek on 2024-12-05
Did you successfully print the test page before you downloaded the driver from the Xerox as apparently indicated in your post?  Did you contact Xerox or go through the FAQ at their site to get information?  The link below is their support site.  If you do not have the box it came in, hopefully you copied the necessary information such as product name or Serial number which you will probably need.

Did you check to see if the install files you downloaded were executable?  You may need to run them as root.

---

### Post by sulani on 2024-12-08
> **yancek said:**
> Did you successfully print the test page before you downloaded the driver from the Xerox as apparently indicated in your post?  Did you contact Xerox or go through the FAQ at their site to get information?  The link below is their support site.  If you do not have the box it came in, hopefully you copied the necessary information such as product name or Serial number which you will probably need.

Did you check to see if the install files you downloaded were executable?  You may need to run them as root.

I printed several test pages using the buttons on the printer. The printer is OK I just cant figure out how to make it connect it properly to the laptop.
 Here are the files from the xerox driver if I run them teh terminal flashes but nothing happens.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294612&stc=1[/IMG]

---

### Post by yancek on 2024-12-08
One thing you can check is to navigate to the directory in which the .sh files reside in the image you posted and run ls -l which will show owner:group and permissions and they should show as executable.  Have you done that.  You could also right click on the various file icons and click properties and in the new window, click permissions to see if they are executable.

Have you tried running the scripts from a terminal after verifying they are executable?  ./install.sh from the directory in which they reside should work.

---

