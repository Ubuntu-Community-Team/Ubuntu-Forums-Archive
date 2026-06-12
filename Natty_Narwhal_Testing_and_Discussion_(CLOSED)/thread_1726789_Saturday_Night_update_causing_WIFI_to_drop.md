---
title: "Saturday Night update causing WIFI to drop"
date: 2011-04-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ShatPank on 2011-04-11
Pretty much as the thread suggests.

Update pretty much daily, and after updating Saturday night, my ALFA 1Watt (RTL8187) adapter keeps dropping my connection as soon as any bandwidth usage happens, even loading web pages occasionally causes it to dis-connect.

Currently I'm using a cheap thing I had laying about (some Ralink rubbish), with no real problems, but I'd like to get my ALFA working again as it provides an ungodly strong connection, and my desktop is not exactly near my router.

If you need to know anything else just ask :)

Stu

---

### Post by ShatPank on 2011-04-12
Anyone? this is a fairly big problem for me as it's my preferred and default WIFI adapter.

---

### Post by ChrisWells on 2011-04-12
I just tried a live cd of 11.04 beta 1, and noticed the realtek bug still exists (for 8168 cards) where it uses the 8169 driver instead and causes the network card to break until the PC's been powered off for ages / CMOS reset. There is a fix I used on 10.10 to use the proprietary driver and another fix to make sure it stays used permanently (after updates etc)

I don't know anything about putting in a bug report, I've not been using Ubuntu for too long, but I do know this bug is years old (afaik) anyone know if this is being worked on? It is major

---

### Post by theanswriz42 on 2011-04-12
Happens on my system as well.

02:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by KegHead on 2011-04-12
Hi!

Have you checked for drivers?

System...admin..additional drivers?

KegHead

---

### Post by cariboo on 2011-04-12
Merged two threads on the same subject.

---

### Post by KegHead on 2011-04-12
Hi!

Just guessing..but could you have lost a connection to your wifi..ie connecting to someone else's?

You can check by clicking on your wifi icon on the top of your screen.

KegHead

---

### Post by theanswriz42 on 2011-04-12
> **KegHead said:**
> Hi!

Just guessing..but could you have lost a connection to your wifi..ie connecting to someone else's?

You can check by clicking on your wifi icon on the top of your screen.

KegHead
That hasn't been the case for me. System shows I'm still connected to the AP but the actual networking stops completely until I reconnect manually.

---

### Post by KegHead on 2011-04-12
Hi!

When is the last time you upgraded?

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

KegHead

---

### Post by theanswriz42 on 2011-04-12
> **KegHead said:**
> Hi!

When is the last time you upgraded?

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

KegHead
I typically upgrade every few hours. The most recent time was about an hour ago. And I rebooted as well.

---

### Post by KegHead on 2011-04-12
Hi!

goto;

Ubuntu docs...WifiDocsWiFiHowTo.

This should help!

KegHead

---

### Post by theanswriz42 on 2011-04-12
> **KegHead said:**
> Hi!

goto;

Ubuntu docs...WifiDocsWiFiHowTo.

This should help!

KegHead
I don't think there's anything in that doc that applies to the bug.

---

### Post by KegHead on 2011-04-12
Hi!

Have you checked with the vendor for updates?

Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)

KegHead

---

### Post by theanswriz42 on 2011-04-12
> **KegHead said:**
> Hi!

Have you checked with the vendor for updates?

Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)

KegHead
I haven't yet gone that route. I've only been running natty for a couple weeks. It was running fine on 10.10 so something obviously changed. 

I'll check out the atheros site though.

---

### Post by KegHead on 2011-04-12
Hi!

Let us know the outcome.

KegHead

---

### Post by ShatPank on 2011-04-12
Sorry, I was out for the afternoon.
Nope, still connecting to MY access point, first thing I checked because window's has a habit of trying to connect to BTOpenZone.

As was said by someone else, the connection doesn't drop, more data stop's moving, I'm still connected to the router (according to ubuntu network manager) but nothing will download, incidentally though, I've noticed on 1 occasion that uploading on torrents was still working.

Again, I also haven't tried checking for vendor driver releases, as the problem only cropped up on Saturday, even though I've been running Natty since Alpha 3 now, problem only started happening after updating saturday. (I also tend to update daily)

stu

---

### Post by ikkefc3 on 2011-04-12
> **ShatPank said:**
> Sorry, I was out for the afternoon.
Nope, still connecting to MY access point, first thing I checked because window's has a habit of trying to connect to BTOpenZone.

As was said by someone else, the connection doesn't drop, more data stop's moving, I'm still connected to the router (according to ubuntu network manager) but nothing will download, incidentally though, I've noticed on 1 occasion that uploading on torrents was still working.

Again, I also haven't tried checking for vendor driver releases, as the problem only cropped up on Saturday, even though I've been running Natty since Alpha 3 now, problem only started happening after updating saturday. (I also tend to update daily)

stu
I have the same problem since a few months with natty with multiple Wifi adapters (Ralink, Realtek and Atheros).

---

### Post by theanswriz42 on 2011-04-12
> **ikkefc3 said:**
> I have the same problem since a few months with natty with multiple Wifi adapters (Ralink, Realtek and Atheros).

Yeah, I have a feeling this is a bigger issue than just a couple cards.

---

### Post by ikkefc3 on 2011-04-13
> **theanswriz42 said:**
> Yeah, I have a feeling this is a bigger issue than just a couple cards.
I have the issue especially when using draft-n/n wifi equipment.
I set up my old bg router and the connection is a lot more stable (almost no download drops).

Old router: Sweex LW050V2
New router: TP-link 1043ND

Wifi adaptor:Atheros AR9285

---

