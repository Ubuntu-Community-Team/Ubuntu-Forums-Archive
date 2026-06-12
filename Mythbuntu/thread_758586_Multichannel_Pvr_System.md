---
title: "Multichannel Pvr System"
date: 2008-04-18
forum: Mythbuntu
---

### Post by nemesys79 on 2008-04-18
Hi everybody, nice to meet you all,

i have to build a system in a lan for viewing and recording multiple channels by web interface.I explain better:

in ny Lan (with NO internet connection), there are about 15 computers where users should have tha ability to choose an analog tv channel (from a maximum of 9 channels), record it if they want, or watch previous recordings made by itself or from other people.

I have this hardware basis:

MythBuntu 0.20.2007
Acer Veriton 460 Desktops
INTEL 2140 PENTIUM DUAL CORE (1.6GHZ,800 FSB,1 MB DI CACHE)
1Gb Ram
160Gb 7200 RPM S-ATA II
Ati radeon x3100
"9" philips saa713x tv pci cards

The system (i think) should run like:

1 Primary backend for streaming the 9 channels
1 or more secondary backend for the 9 pci card

I'm trying to learn something from various manuals i find around,i'm new to mythtv...:confused:

Can you please help me in designing this system?

Myth TV Rocks:guitar:....I Hate mce...

---

### Post by volkswagner on 2008-04-18
What other purpose would these workstations serve?  Will they be powered on 24/7?  Will 15 units be used at the same time?  Can the master get internet for programming guide?  You should start by running the Mythbuntu live CD to see how well the basic hardware behaves.

---

### Post by nemesys79 on 2008-04-21
> What other purpose would these workstations serve?
Nothing more than watching tv e record preferred channels

> Will they be powered on 24/7? 
yes they will

> Will 15 units be used at the same time?

yes,most af all at the same time

>  Can the master get internet for programming guide?
No, at the moment.I know it's a big limitation but that's what my lan can provide now.

Thank you!:)

---

### Post by volkswagner on 2008-04-21
I would suggest install the master backend with one or no tuners.  This will allow max power for serving the database.  Look into diskless boot.  If you can get diskless going,  you can have less slaves by putting multiple tuners and harvested hard drives.  The frontend only machines can be powered off without effecting available content.  Also look into cloaning.  This can save config time since you are dealing with identical hardware.

---

### Post by nemesys79 on 2008-04-21
So you say that i'll have about 3 or 4 machines, one of them is the master backend, the others will be secondary backend, right? The scheme would be that secondary backends with "n" tuners installed will stream the channels to the primary backend, and the primary will stream itself to the 15 frontend via web broser in http (MythWeb).

At the moment i'm trying to install 2 cx23880 based tuners on the first machine (it will be one of the backends)

I think it's installed properly,myth setup recognizes them like v4l2 based cards,but i can't start the database (i type mythfilldatabase option but my db can't connect,so i have no channels....

:DThank you for your support

---

### Post by volkswagner on 2008-04-21
The first machine needs to be the master.  I am using my phone, so I can't post links.  You need to access to mysql.  If you changed mysql password from the default, you will need to "tell" mysql.  When setting up your tuners, follow all steps in backend setup.  Since you have on schedules direct lineup, when you scan for channels they will all be named unknown.  For location of database server use localhost.  On all other machines enter use ip address of the master.  Setup static ip addresses for all machines in network manager.

---

### Post by nemesys79 on 2008-04-23
Ok, i'll make some tests today and i'll let you know...TNX

---

### Post by nemesys79 on 2008-04-28
ok now i have the right connection to the db,my tuner is properly installed but i can't no channels during scanning...antenna cable is ok.Does anyone know how to test this conexant cx tuner?

---

