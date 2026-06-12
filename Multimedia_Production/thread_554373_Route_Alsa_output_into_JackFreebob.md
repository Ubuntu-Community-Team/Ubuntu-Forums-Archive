---
title: "Route Alsa output into Jack/Freebob"
date: 2007-09-18
forum: Multimedia Production
---

### Post by miltonics on 2007-09-18
The only way that I can get sound on my computer is to use Jack with freebob.

I'm trying to find a way to enable all the programs that can't use jack directly, to somehow pipe their output into jack.  I'm thinking that somehow alsa could be a connection in jack?

If I use the alsa driver under jack then I won't have any sound.

---

### Post by Stochastic on 2007-09-19
I read a page from a google search on the matter not to long ago that claimed by editing an asound config file that you could route the output of alsa into jack.  I briefly tried it but had no luck so I tossed the hack and have made do with the onboard audio for any non-jack apps.  The one that I was successful at was Amarok as you merely compile the newer xine from cvs to get jack support.

---

### Post by 00l0 on 2007-09-25
> **Stochastic said:**
> I read a page from a google search on the matter not to long ago that claimed by editing an asound config file that you could route the output of alsa into jack.  I briefly tried it but had no luck so I tossed the hack and have made do with the onboard audio for any non-jack apps.  The one that I was successful at was Amarok as you merely compile the newer xine from cvs to get jack support.

i'd love to read that page, do youby any chance still have the link?

thanks : D

---

### Post by Stochastic on 2007-09-25
well if you do a google search for:  asound jack
there's quite a few results, that being said, I'm not sure how many of them work.  If you're successful please let me know how you did it as I have a freebob/ffado device as well.

---

### Post by xdissent on 2007-10-18
I too had the same problem. I just figured it out today and haven't gotten a chance to try it yet, BUT what you want is the alsa_connect utility from the netjack package. Not even sure if there IS a package for it so you might have to build from source, but that should be cake. The way jackd works currently, there can only be one backend client - in your case, freebob (ffado in mine) but many frontend clients. Most people use the alsa backend client for piping alsa to jack because they don't need firewire support. Torben Hohn wrote netjack and included alsa_connect as a frontend client for alsa's output because obviously he assumes you're using the netjack backend. Anyway, killer app - hope it works.

---

### Post by distort on 2007-10-19
I successfully used these instructions to pipe alsa output through jack:

[http://alsa.opensrc.org/index.php/Jack_%28plugin%29](http://alsa.opensrc.org/index.php/Jack_%28plugin%29)


Make sure you have the alsa-plugins package installed before you try it.

---

### Post by jgrealish on 2007-11-16
Sorry for the bump!

I've searched my directories high and low for asoundrc and was unsuccessful. Do you create a new asoundrc file? And, if so, where do you place it? Or, did I miss something (probably)?

jgrealish

---

### Post by octoberdan on 2008-04-23
> **jgrealish said:**
> Sorry for the bump!

I've searched my directories high and low for asoundrc and was unsuccessful. Do you create a new asoundrc file? And, if so, where do you place it? Or, did I miss something (probably)?

jgrealish

Checkout: [http://alsa.opensrc.org/index.php/Asoundrc](http://alsa.opensrc.org/index.php/Asoundrc)

You'll have to create it :-p.

If you have any other questions, don't hesitate to ask.

---

### Post by hogiewan on 2008-06-23
distort - I don't see an alsa-plugins package in the repositories, and I get get errors on ./configure from the download.  

octoberdan, should I say "Phi Alpha"?

---

### Post by kendase3 on 2008-07-23
So I was curious if anyone's made any progress since a month ago, since I use my headphones connected to my firebox on my windows partition for general sound and would like to be able to do the same on Ubuntu.  I've set up the headphones to work with qjackctl and ardour, those work fine, but I'd like to set it up so that alsa is redirected through to freebob without me having to establish the connection on a program by program basis.  Is such a thing possible?

---

