---
title: "select not changing channels on program guide"
date: 2008-02-05
forum: Mythbuntu
---

### Post by mikedirl on 2008-02-05
Hi,

I posted this over in [www.mythtvtalk.com](www.mythtvtalk.com) but nobody had any ideas so I decided to post here as I am running Mythbuntu.

Firstly some info about my setup.

I am currently running Mythbuntu 7.10 (which has mythtv 0.20.1 i think).
I am based in Ireland and use XMLTV to grab the program data.
I use an MCE remote.
The frontend and backend are running on the same computer.
I have a SKY set top box and I control this using a device called dusky control. I use this because it is more reliable than an IR transmission solution. I have a script which takes the channel number as a parameter and calls the dusky control device. This is set in my backend as the external command to run when changing channels.

Nearly everything is working perfectly, when I watch TV I can change channels using the up and down arrows on my remote. Mythtv sends the commands to the set top box and the channels change correctly.

The problem arises when I go into the program guide from watching tv and scroll to a channel to watch. I want the select button on my remote control to change channel.

By default when I pressed select it brought up the recording options.

I then read that to change this behaviour I had to set the **use select to change channel in the programme guide** option. I did this but now when I press the select button on the program guide the system just returns to the tv picture without changing channel.

The thing that really gets me is how can the up/down button on remote change channel in watch tv mode (sort of proves that the setup is correct) but not select from the program guide. I am beginning to think this must be a bug in myth tv (I hope not).

I have already spent two weeks looking at settings and searching the web for a solution.

Can anybody help me find a solution?

---

### Post by mikedirl on 2008-02-06
I found what was causing the problem.

I had assigned channel numbers with leading zeros.

001, 002, 003 etc

When I changed these to 1,2,3 etc it works.

---

