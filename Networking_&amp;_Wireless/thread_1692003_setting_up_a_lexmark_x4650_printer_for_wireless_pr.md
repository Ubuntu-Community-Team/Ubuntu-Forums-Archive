---
title: "setting up a lexmark x4650 printer for wireless printing with 64 bit ubuntu"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by charlieluna on 2011-02-20
I have a 64 bit laptop and i am using the 64 bit version of ubuntu 10.10. i am wanting to setup a lexmark x4650 printer which has wifi built in and can do wireless printing. i have the driver from lexmark installed but it is the i386 version which i know is the 32 bit version. and i know that 32 and 64 bit versions don't work so well together. i've gone through all kinds of help on these forums and for some reason when go to print a test page, it comes back with an error statement. i will have to try it again so i can post it verbatim.

i have a similar thread in the 64 bit thread so if it can be locked or deleted and have just this one, that would be cool. 

this same printer is not connected to any computer for it's wireless printing ability. it is a stand alone but all of my families laptops can use it since they have the software on theirs. they are using windows 7 which is what i have also, but i am switching to linux since i am not a fan of microsoft at all. i despise everything they do. i love linux and the community around it and i just want to get this printer setup so i can make the last and final switch. this is the only thing holding me up. please help.

---

### Post by charlieluna on 2011-02-22
bump, just trying to get someone to notice this.

---

### Post by charlieluna on 2011-02-22
Hey everyone!! I just got my printer working wirelessly!! SOLVED!!!

---

### Post by John_Howarth on 2011-03-05
Hi Charlieluna, congratulations on getting your printer working on your 64bit Ubuntu. How did you do it? Thanks.

---

### Post by John_Howarth on 2011-03-05
OK, too quick to post there! Here's what I did for the benefit of those who are like me and new to Ubuntu/Linux.

I added a network printer (under System | Administration | Printing) by typing in the X4650's IP address. The system detected it as using a Jet Direct card.

I then selected Lexmark 3600-4600 from the driver options.

---

### Post by charlieluna on 2011-03-05
> **John_Howarth said:**
> Hi Charlieluna, congratulations on getting your printer working on your 64bit Ubuntu. How did you do it? Thanks.

It was actually not really hard. But it just takes a little bit. here goes what i did.

1. First thing i did was to change the administrator password to something i know. I opened a terminal and used "sudo passwd" and it was really easy.

2. Once that was done, I downloaded the driver from lexmark. I ran it, put in the admin password, and followed the instructions even up to the point of connecting the printer to my laptop via usb cable. but this doesn't mean that will need to be hooked up to print. 

3. I unhooked my laptop. and then proceeded with the next phase.

4. this next phase requires you to be at the printer. on the control panel, push the setup button. arrow over to find the network setup option. press ok.

5. arrow over to find TCP/IP. push ok. 

6. arrow over to find IP address. press ok. this will give you the ip address of the printer. write it down.

7. go back to your laptop and click on system. highlight administration and then click printing in the menu.

8. in the new window, click on server. highlight new and then click on printer.

9. in the new window, click network printer. then click find network printer. 

10. on the right side, put the ip address in the text box for host. click find. it should find it and download the driver. i know, you might be thinking redundant but it is necessary. i tried it without downloading the driver first and it wasn't in the list of models you can choose from. after i downloaded the driver from lexmark and went through this process again, the model was there. 

11. it should pull up a list of manufacturers now and you can choose lexmark. then choose the 3600-4600 model since the x4650 belongs in that category. 

12. it will display a few names for your pc and the printer and just keep clicking forward and it will be done eventually. 

13. you should be able to print wirelessly now. 

good luck and enjoy!!

---

