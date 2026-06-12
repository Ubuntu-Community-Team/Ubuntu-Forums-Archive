---
title: "Does anyone have Component Video working?"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by RDV on 2007-10-25
NOTE: This posting has also been posted on Phoronix AMS/ATI Linux driver forum. It did not get any replies so far.
------------------------------------------------------------------------------------------------------
I am trying to get my ATI X1800 displaying on my HDTV through my cards Component Video cables.

I am running:
Ubuntu 7.10 Gutsy
ATI 8.42.3 drivers

My crt1 runs perfectly including Compiz 0.10.3

Also ATI Catalyst Control Center runs but does not display any HDTV supported formats for me to select.

I know that my Component video (cv) does not return any EDID information from the /var/log/Xorg.0.log

I have tried a number of combinations for the command line:
--add-cvmode=WIDTH,HEIGHT,FLAGS,BASEWIDTH,BASEDHEIGHT,RE FRESH.

All of the combinations "fail" and therefore are not added to my xorg.conf

At times I have forced "TV" on but that also has no effect.

My /var/log/Xorg.0.log shows that Component Video is detected but gets disabled:
(II) fglrx(0): Connected Display2: Component Video [cv]
(II) fglrx(0): Display2: No EDID information from DDC.
(II) fglrx(0): Display2: Failed to get EDID information.
(WW) fglrx(0): DALEnableDriverInstance on secondary failed: 9
(II) fglrx(0): For single mode, Component Video is disabled

What I would like is better documentation for "aticonfig" option:
--add-cvmode=WIDTH,HEIGHT,FLAGS,BASEWIDTH,BASEDHEIGHT,RE FRESH.

What are "FLAGS" and what are valid values? An example or two would go along way.

I have assumed the option would like something like:
aticonfig --validate-cvmode=1280,720,0x00,1280,720,60.0

That one failed but 1280x720@60Hz works no problem under Windows Vista. In fact under Windows Vista the ATI Catalyst Control Center makes displaying on my HDTV a snap.

Any help would be appreciated.

---

### Post by RDV on 2007-10-25
As I have not received any forum help to get my HDTV connected via the Component Video I opened a ticket with ATI support requesting the following:
1) Better aticonfig documentation for “--validate-cvmode” argument including a few examples. Examples are the most important.
2) A “xorg.conf” file for a working component video configuration. (e.g. crt1 and a component video 1280x720p@60Hz HDTV output)

The support ticket details included most of the information in my Ubuntu posting above. I also added the incentive that I would post ATI’s response on Phoronix and Ubuntu forums so that it would reduce additional support tickets.

Here is the first response to the support request:
----- Original Message -----
From: AMD - Customer Care
To: my email address
Sent: Thursday, October 25, 2007 10:32 AM
Subject: Ticket #737-1282161 (How-To for Component Video output)

The Linux drivers available from ATI are provide are "as is".
You may be able to get further assistance from the Linux community
at the links below:

[http://www.linux.org/help/index.html](http://www.linux.org/help/index.html)

[http://www.linuxdoc.org/](http://www.linuxdoc.org/)

[http://www.xfree86.org/](http://www.xfree86.org/)

To report issues with Linux drivers you can submit an online ticket using
the "Linux Driver Feedback" Category, and your report will be
received and reviewed/tested by our driver team. Please note that your report
will only be responded to if we require additional information.


Ticket Information:
Ticket #: 737-1282161
Date Created: 10/25/2007 10:30 AM EDT
Category: Solve a Problem
To update or check the status of this Ticket:
- Go to: [http://support.ati.com/ics/support/d...cketID=1282161](http://support.ati.com/ics/support/d...cketID=1282161)

- Log in, and you will be automatically taken to the Ticket page.

Customer Care
ATI Technologies Inc.
ati.com
------------------------------------

Ok, I already understood that the drivers are “as is” but I wanted to know how a feature that is suppose to work in ATI’s own driver release notes is set up. As requested I re-submitted the same information request as a “Linux Driver Feedback” ticket. I just received an auto-response:

Dear AMD Customer,


This is an Auto-Response based
on the fields you selected when submitting your Ticket. Our Auto-Responses
resolve most of our customer’s queries.

Please try the suggestions below in order to resolve the issue you are
facing.

To respond to your ticket, visit [http://support.ati.com](http://support.ati.com) and
login to “My Support.”




SOLUTION
Information about Linux support for Radeon and All in wonder products can
be found in link below:
[https://support.ati.com/ics/support/...estionID=28027](https://support.ati.com/ics/support/...estionID=28027)
If the information above does not resolve your issue, please respond to your
ticket in order to get assistance from our qualified support representatives.
Thank you for choosing AMD!

AMD Global Customer Care for ATI products

Ticket Information:
Ticket #: 737-1282171
Date Created: 10/25/2007 11:09 AM EDT
Category: Linux Driver Feedback
To update or check the status of this Ticket:
- Go to: [http://support.ati.com/ics/support/d...cketID=1282171](http://support.ati.com/ics/support/d...cketID=1282171)

- Log in, and you will be automatically taken to the Ticket page.

Customer Care
ATI Technologies Inc.
ati.com
-------------------------------------

I am left shaking my head. The web linked referenced in the response above contains 4 other web links. The first is to information that has not been updated since 2004 and the second is a dead link the last links are generic Linux sites.

If AMD/ATI is serious about Linux support it can at least provide adequate information on features ATI claims that it’s drivers support. To test a feature they would have to have information on my two requests.
1) Better aticonfig documentation for “--validate-cvmode” argument including a few examples. Examples are the most important.
2) A “xorg.conf” file for a working component video configuration. (e.g. crt1 and a component video 1280x720p@60Hz HDTV output)

I just hope an AMD/ATI driver developer sees this posting and responds. As I have observed I am not the only one asking these questions.

I have update both tickets stating that the responses did not help. I do not have much hope but at least the tickets are still open.

---

### Post by methane on 2008-01-25
Hi RDV,
I'd love to know if you ever got this working.  I'm about to try the same thing.  I know that my card works fine in Ubuntu with the restricted drivers.  But I don't know where to begin getting it to turn on the component video using the s-video-like dongle.  
If you've got any advice, that would be great.

Thanks,
Brad

---

### Post by RDV on 2008-02-22
I finally got HDTV Component video working. I switched to Nvideo (GeForce 8600 GTS). With "Sync to VBlank" turned on in the NVideo control panel (2 places) and in Compiz-Fusion Config Settings Manager "General Options/Display Settings", I get Compiz-Fusion and NO video tearing.

Now that I can display Linux on my HDTV I have fully switched to Ubuntu dumping both Microsoft and ATI.

---

