---
title: "Routine Updates Kill Network Connections"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by WrkWatchr on 2011-11-01
I am a newbie who had help setting up a Dell 2950 Server running Lucid 10.04 LTS as a NAS/MediaServer. For the last year it has run like a charm and had no problems. Approximately every 2 weeks I install the recommended updates and until now - no problems. However, Last week when I did this I now find I have NO network connectivity. 

During the BIOS Boot I can see the network assigning a DHCP address to the server for use if I was using the network boot option (I don't).

The system boots normally, but when I enter my password to open the server - NO NETWORK CONNECTIONS. The servers have 4 separate GB network cards and to see if I had a bad card, I plugged all cards into a new GB switch. All 4 connections (etho-eth3) show they try to connect but refuse to pick up a DCHP/connection. 

A friend recommended I try running with a former Kernal option upon bootup but the system goes right into the "pink" Lucid login screen with no grub options. I am getting used to SAMBA problems but without a connection I cannot even blame SAMBA. 

STEP-BY-STEP Help would be appreciated. 

Roy

FYI - I can verify I have good connectivity at the cable connecting into my server using a windows laptop so I know the network is working as expected.

---

### Post by WrkWatchr on 2011-11-02
Solved...nothing wrong with updates. Updates were just a timing coincidence. Problem created by 5 yr old who plugged in an extra wire into my switch creating DHCP errors- Thanks to all who tried to help

---

