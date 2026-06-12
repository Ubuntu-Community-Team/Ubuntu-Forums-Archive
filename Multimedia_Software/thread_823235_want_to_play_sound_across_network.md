---
title: "want to play sound across network"
date: 2008-06-09
forum: Multimedia Software
---

### Post by toby_1_kenobi on 2008-06-09
I have Ubuntu 8.04 Desktop on one computer and Ubuntu 8.04 server on another. I want to make the audio from the desktop computer come out of the speakers on the server across my LAN. I understand this is possible with Pulse Audio.

I have downloaded and run pulseaudio on the server. I have modified the default.pa file on the server (attached) and I have allowed port 4713 in the firewall. I have also selected all the checkboxes in the network access tab of pulsaudio preferences on the client. I have installed padevchooser and when I run it it detects my server as an option for server, sink and source. I select these options. But still when I play sound from gnome it comes out of my local speakers.

What am I missing?:confused:
By the way, don't ask me to use a gui tool on my server.

---

### Post by jocko on 2008-06-09
I think pulseaudio uses a file called .pulse-cookie (hidden in your home directory) to determine permissions for allowing incoming sound streams.
Try copying the .pulse-cookie file from your desktop to your server, and then restart pulseaudio  on the server.

---

### Post by toby_1_kenobi on 2008-06-11
I think I made a mistake before, thinking I was selecting the server as default server in padevchooser when I was actually selecting the desktop. The server isn't actually showing up as one of the options.

I copied .pulse-cookie to the server I put it in /home/myuser then restarted pulseaudio with ```
sudo /etc/init.d/pulseaudio restart
```

In padevchooser I selected "other" for default server and entered ```
tcp:<ip-of-server>:4713 <name-of-server>
``` but that makes no sound happen at all (I figure if it's not coming out of the desktop speakers I'm half-way there)

---

