---
title: "My Dual Monitor Tactic...."
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by u10 on 2008-03-23
With the help of a lovely forum, I figured out this dual screen issue…. Here’s the deal folks…. As simple as I can make it.
If you are using the Nvidia Drivers and Ubuntu Gutsy do the following to get two monitors to work on a laptop. Here’s how you do it in plain English. Before you start make sure etc/X11/xorg.conf is clean.

1. Download the Nvidia Drivers/Envy from the Add/Remove Programs. This requires some research to know which ones you need depending on your card.

2. Make sure you know both resolutions you are shooting for. If you have windows you can check there very easily. There’s a command out there for the terminal within ubuntu.

3. Set up your monitors just as you would in windows using ‘Screen and Graphics’, extending

4. Log out, Login…

5. Don’t freak out. My system was stuck stretching the primary monitor ac cross to the secondary monitor at a huge resolution.

Here’s the TRICK

6. open the terminal and type

sudo nvidia-settings.

edit the multiple display to mimic the one in screens and graphics.

Turn OFF Xinerama.

Click Save to X Configuration

Quit

Restart.

When you login you will get two screens that you can’t drag windows back and forth to but at least there’s two.

If you get that far successfully and are running compiz and emerald you’ll notice that your window title bars are missing on the new secondary screen. So solve this go into the compiz’s settings, make sure monitor “1&#8243; is selected on the right, click on the Window Decorations panel where it says command, enter “emerald”.

Restart and you should see emerald.

There’s one more glitch I am working through….

One cube works on the laptop monitor and the cube works on the secondary but when you edit the number of columns for the workspace it only changes the primary monitor.

Hope this posting helps.

-cheers

---

