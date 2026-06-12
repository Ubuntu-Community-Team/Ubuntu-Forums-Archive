---
title: "MythTV Firewire, SA3250, Ubuntu 8.10, can't watch live TV, can't record, can't fillda"
date: 2009-02-21
forum: Multimedia Software
---

### Post by david_tay on 2009-02-21
I have been trying to install firewire and MythTV 0.21 on my Ubuntu 8.10 system for two months now. I am a noob in Ubuntu.

I have a Scientific Atlanta SA3250 set top box. I have a Rosewill Firewire PCI card.

Everything indicates that there's a signal coming from the firewire port on the STB into my pc. 

I ran plugreport which says that there is indeed a signal. 

In mythtv-setup (the backend setup), the capture card appears to be correctly configured and connected to my video source. For my video source, I use EIT for my listings grabber and the default channel frequency table.

However, mythfilldatabase is not filling mysql with any channel information from my STB. In the logs, it says that "Source 1 configured to use only the broadcasted guide data. Skipping." 

On the frontend, when I select "Watch TV", a blank screen flashes for one second and dumps me back to the main menu. In the logs, it says "TV Error: LiveTV not successfully started."

However, I am confident that my firewire is set up correctly (after almost 2 months of pulling my hair out). In the mythfrontend, when I select Information Center:System Status:Tuner Status, it says that "Tuner 1 is not recording" whereas previously it would just say "Tuner 1 is not available." I assume that Tuner 1 is the correctly configured capture card I set up in the backend.

Does anybody know what is going on? I have spent so much time on this I am about to go back to Windoze.

---

