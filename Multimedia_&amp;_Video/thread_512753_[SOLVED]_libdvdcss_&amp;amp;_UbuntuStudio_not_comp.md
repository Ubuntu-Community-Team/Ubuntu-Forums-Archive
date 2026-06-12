---
title: "[SOLVED] libdvdcss &amp;amp; UbuntuStudio not compatible?"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by BobSongs on 2007-07-29
[FONT=Arial Black][SIZE=4][COLOR=Gray]the skinny[/COLOR][/SIZE][/FONT]
[FONT=Verdana] Playing DVD movies in UbuntuStudio does not work.[/FONT]

[FONT=Arial Black][SIZE=4][COLOR=Gray]the long-winded affair[/COLOR][/SIZE][/FONT][LIST]
[*][FONT=Verdana]I live in Canada. The DVD codec is not an issue.[/FONT]
[*][FONT=Verdana]The DVD codec worked in Breezy and Dapper. I skipped Edgy to plunge into Feisty. It works fine there too.[/FONT]
[*][FONT=Verdana]Decided to add the UbuntuStudio-desktop and DVDs stopped playing.[/FONT]
[*][FONT=Verdana]Downloaded UbuntuStudio[/FONT]
[*][FONT=Verdana]Wiped standard Feisty[/FONT]
[*][FONT=Verdana]Installed UbuntuStudio[/FONT]
[*][FONT=Verdana]Installed the DVD codecs via Automatix2 (as per usual). No go.[/FONT]
[*][FONT=Verdana]Booted using the standard kernel. Still: no go.[/FONT][/LIST][FONT=Verdana]Any other UbuntuStudio users run into this problem?

Some of us use Automatix; others hate it. I'm not here to bash or praise it. It just works for what I need after a wipe and install. My family don't want me tinkering in front of the PC any more than I have to. Automatix does the job. But if I need to add the codecs manually, that'll do fine. Just wondering if anyone has encountered this before.

If you need my PC specs:[/FONT][LIST]
[*][FONT=Verdana] Celeron 1.7 GHz[/FONT]
[*][FONT=Verdana] 512 Mb RAM[/FONT]
[*][FONT=Verdana] NVidia GeForce 2 MX 400[/FONT][/LIST][FONT=Verdana]It's all worked before. It's not the card. When booted into XP (I need it for business, don't get hostile ;)) it works just fine.

I await your experience. :-)
[/FONT]

---

### Post by justin whitaker on 2007-07-29
Try the Medibuntu repos instead. I installed it without issue on Gutsy from there, so you shouldn't have an issue either.

---

### Post by BobSongs on 2007-07-29
[FONT=Verdana]> **justin whitaker said:**
> Try the Medibuntu repos instead. I installed it without issue on Gutsy from there, so you shouldn't have an issue either.

Cool! I will do that. Sorry for the delay. I was testing software called PiTiVi.

Uhm. Forgive my utter stupidity: where/how would I add the Medibuntu repos?

*tucks tail between legs and sits quietly*

Edit: Wait! Don't bother. I found this from Google:
[/FONT]```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by SeanHodges on 2007-07-29
I'm not sure if your problem lies in not being able to install libdvdcss, or if it installed OK but you still cannot play DVD's, but if it's the latter:

There is a "bug" in Feisty (and I believe the Ubuntu Studio derivative as well) which means that while you can run a DVD by launching it using the HAL auto-start dialog  that appears when you insert the DVD... but you cannot launch it using the File menu in Totem. There are 2 ways around this if it's the case:

- Always run DVD's using the auto-start dialog. I don't know if this is turned on in UbuntuStudio, but if it is you might find using the dialog will actually start your DVD's in Totem without a problem.

- Use a video player other than Totem for playing DVD's. The VLC player should pick up libdvdcss and work without a problem,  I prefer Kaffeine as I feel it has a nicer interface.


Regards,

Sean

---

### Post by BobSongs on 2007-07-29
OK. Added the Medibuntu repositories but... now what? Forgive my ignorance. A little hand holding here would be good. Once it works: trust me. I won't ask again.

:-)

---

### Post by BobSongs on 2007-07-31
> **SeanHodges said:**
> I'm not sure if your problem lies in not being able to install libdvdcss, or if it installed OK but you still cannot play DVD's, but if it's the latter:

There is a "bug" in Feisty (and I believe the Ubuntu Studio derivative as well) which means that while you can run a DVD by launching it using the HAL auto-start dialog  that appears when you insert the DVD... but you cannot launch it using the File menu in Totem. There are 2 ways around this if it's the case:

- Always run DVD's using the auto-start dialog. I don't know if this is turned on in UbuntuStudio, but if it is you might find using the dialog will actually start your DVD's in Totem without a problem.

- Use a video player other than Totem for playing DVD's. The VLC player should pick up libdvdcss and work without a problem,  I prefer Kaffeine as I feel it has a nicer interface.


Regards,

Sean[FONT=Verdana]
Thanks, Sean.

Here's what I did in case others want to know.

I had done so much installing of stuff that I figured: "Let's start afresh." I've got Feisty on **its own partition** and the **/home folder** on it's own partition. So wiping Feisty is a matter of two lost hours (*not much was installed and the /home folders are not affected, in my case*).

Then 1) I installed UbuntuStudio (Feisty), 2) installed the updates, 3) installed Automatix2, 4) installed the codecs and then 5) told the family to just insert the DVDs to make a film play. It works 100% fine.

Thanks again, Sean. The secret was: **Don't Panic.**[/FONT]

---

### Post by SeanHodges on 2007-08-02
Sorry for my late reply.

Good to hear you're playing DVD's OK now. Hopefully the next release will have fixed this issue (its in the bug tracker), so you won't need to do rely on the auto-start dialog to play the DVD's.


Regards,

Sean

---

