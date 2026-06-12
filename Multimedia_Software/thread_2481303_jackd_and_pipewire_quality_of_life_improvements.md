---
title: "jackd and pipewire quality of life improvements"
date: 2022-11-25
forum: Multimedia Software
---

### Post by DVoid on 2022-11-25
Hi, I'm not sure how many people do pro-audio here, but I've written up a quick tool to assist with running jackd applications on pipewire.

Pipewire is a great product, but some digital audio workstations and other tools crash if pipewire changes sample rate in the background.

So those tools need to be launched a certain way with the pipe-wire command line helper scripts.

I've written a front end based on the same intentions of the old and excellent qjackctl interface into jackd. It uses the pipe-wire helper scripts and presents them in a gui.

It's simple but it helps me a bit, so I'm popping a link to the github repository here.

Hope it helps someone.

Instructions and the app are here:

[https://github.com/ginoputrino/pipejackctl](https://github.com/ginoputrino/pipejackctl)

[IMG]https://github.com/ginoputrino/pipejackctl/blob/main/images/pipejackctlScreen.png?raw=true[/IMG]

---

