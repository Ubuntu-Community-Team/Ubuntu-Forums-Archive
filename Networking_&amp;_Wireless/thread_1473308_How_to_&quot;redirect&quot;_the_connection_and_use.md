---
title: "How to &quot;redirect&quot; the connection and use telephone as proxy, wvdial issues?"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by El Potro on 2010-05-05
Hi, please forgive my lack of terminology as I'm not an expert.
First, I explain my situation:

What I want to do is to share the internet connected to a computer with a telephone, over another telephone which is permanently connected to the pc.

The thing is, that some guys found a way of making this on windows, in fact, I already set it up on xp and works like a charm, it involves configuring in a certain way the telephone, and to use 2 programs. One is CCProxy, which redirects the internet connection to the telephone, and another one, which updates the IP adress of the telephone connection to dyndns, so that I can put that adress on my second telephone as proxy, and this way, surf on the net through my home internet on the telephone anywhere. Tricky right?

Now, the thing is I don't like at all booting windows only for sharing internet with my telephone. So I want to do it in linux. I use Ubuntu and Puppy linux home.

I tried setting up the connection to the modem with wvdial, and... I got connected! But hey, when I connect to the telephone, I lost my internet connection (main, cable based, the pc connection) :-S. I mean, somehow, the "active" connection for the browsers and all the internet programs is now the connection I have made with my telephone, which is plugged to the computer.

Now my objective here is that NO CHANGE of active connections get done when I start the connection to the phone, and then, get a program like CCProxy, and a dyndns updater for sharing the internet connection on the pc, to the connection made on the telephone-modem wired to the computer.

Am I clear? I know it is confusing, and it took me weeks to understand how it works and get it done in windows. But now... Ubuntu is what I want.

Any ideas?

Thank you all very much,

Mauricio

---

### Post by El Potro on 2010-05-05
The situation is this:

The computer is connected to a hub, which is also connected to a modem/router, which manages the connection to internet (ADSL).

Now I plug a telephone through USB to the computer, and I start using it as a modem, I mean, not to use internet, but to share through that connection the connection I'm using on the computer (ADSL)

Is it clearer? If I had money enough and didn't have the ADSL, through the phone you are able to connect to the internet, but here, costs much...
So what I did is, I found a way of configuring the telephone (using as APN the mms server), and with the same configuration on a second phone, plus some programs (CCProxy), I'm able to use the connection of the computer (ADSL) that passes to the telephone which is being used as a modem that sends the info to the mms server of the company, so, when I connect to the mms server on the second phone, I can use the ADSL in the telephone.

Tricky, I know but saves money.

Please, anybody, what I'm asking here, is how to route (I think that is the correct word) the connection I get from the router/modem (ADSL), to the PPPoE connection, that is made to the telephone which is being used as modem.

Am I clearer?

Thank you for pitching in, really appreciated!

---

