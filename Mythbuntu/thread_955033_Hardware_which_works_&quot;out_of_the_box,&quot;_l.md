---
title: "Hardware which works &quot;out of the box,&quot; like on the box?"
date: 2008-10-21
forum: Mythbuntu
---

### Post by R3M3 on 2008-10-21
Background:
Because of the upcoming US switchover to digital TV, I'm thinking about replacing my VCR with a PVR. As all the commercial ones require monthly service fees, I'm looking into turning an (2-3 year) old computer into a MythTV box. I figure I need a tuner card and a remote, at the least. (An extra hard drive and a DVD burner* will probably also be added.)

Unfortunately, attempting to spec out a low-cost tuner card and remote is an exercise in frustration. While I've found the list of "supported" cards at linuxtv.org, the list doesn't really help. If the cards is not no longer sold, it requires a kernel recompile, or there is some feature which isn't really supported (e.g. the composite input doesn't work on Linux), or there is some bizarre hardware contortions to make it work (e.g. needing to patch externally to the sound card in order to get sound). This, of course, assumes that you can actually find a description of how well the card works on Linux in the first place, as opposed to an empty/missing page, or just some incomprehensible (to me) settings dump.

Then there's the remote. Who knows if the remotes that come with the card will work on Linux? It might say on the card's linuxtv.org, but probably not. If you want to use a separate remote, there's lirc.org, but I can't find an understandable (to me) list of supported remotes. At any rate, LIRC looks like it's only for home-brew IR receivers. I don't think there's any information about compatible commercial USB remote/receiver pairs.

Any rate, my question: Are there any ATSC tuners out there that work on Linux "out of the box", without any significant software/hardware contortions, and for which there isn't any feature missing in Linux that one would think should be there due to the product description, and that one can still purchase from a major electronics retailer (i.e. no ebay/craigslist/TunersFromTheBackOfATruck.com)? Same question for remote controls. Oh, and I'd prefer to spend as little as possible, if possible.

*(Although with the headache I've gotten from trying to find tuners/remotes, I'm concerned that using a DVD reader/burner on Linux is probably going to have it's own issues.)

---

### Post by mrand on 2008-10-22
> **R3M3 said:**
> Background:
Because of the upcoming US switchover to digital TV, I'm thinking about replacing my VCR with a PVR. As all the commercial ones require monthly service fees, I'm looking into turning an (2-3 year) old computer into a MythTV box. I figure I need a tuner card and a remote, at the least. (An extra hard drive and a DVD burner* will probably also be added.)

Unfortunately, attempting to spec out a low-cost tuner card and remote is an exercise in frustration. While I've found the list of "supported" cards at linuxtv.org, the list doesn't really help. If the cards is not no longer sold, it requires a kernel recompile, or there is some feature which isn't really supported (e.g. the composite input doesn't work on Linux), or there is some bizarre hardware contortions to make it work (e.g. needing to patch externally to the sound card in order to get sound). This, of course, assumes that you can actually find a description of how well the card works on Linux in the first place, as opposed to an empty/missing page, or just some incomprehensible (to me) settings dump.

Then there's the remote. Who knows if the remotes that come with the card will work on Linux? It might say on the card's linuxtv.org, but probably not. If you want to use a separate remote, there's lirc.org, but I can't find an understandable (to me) list of supported remotes. At any rate, LIRC looks like it's only for home-brew IR receivers. I don't think there's any information about compatible commercial USB remote/receiver pairs.

Any rate, my question: Are there any ATSC tuners out there that work on Linux "out of the box", without any significant software/hardware contortions, and for which there isn't any feature missing in Linux that one would think should be there due to the product description, and that one can still purchase from a major electronics retailer (i.e. no ebay/craigslist/TunersFromTheBackOfATruck.com)? Same question for remote controls. Oh, and I'd prefer to spend as little as possible, if possible.

While I don't have one yet (since I don't have HDTV), the HDHomeRun is the unit that everyone holds up as the example.  It probably helps that the company even supports its use with Linux.  There are obviously other tuners that work well - just read/search through the posts here and/or on the mythtv-users list.

LIRC isn't just for home-brew.  While it is certainly very common for home-brew, there are a metric ton (x100) more people that use it for off-the-shelf remotes, made by companies ranging from ATI to Wintek.  [Here is the complete list]("http://lirc.sourceforge.net/remotes/").  Most people seem to be migrating towards Media Center Edition remotes - most any of them will work, but if you want increase your probability of success even higher, you can do one of two things: search to see if people have successfully used it with lirc, or select one that is based upon one of the designs in the list below.  Note that I said "based upon" - these types of things are re-branded a ton, so the name on the remote may be some random characters, but _nearly_ all should be using one of the below designs.

As for the monthly fees: If you are using it just as a VCR replacement, you don't need schedule stuff, but to get the full power of a PVR, you have to get schedule information from somewhere.  Your choices are to subscribe to listing service ($20/yr for schedules direct), scrap from web sites (problematic), use EIT, or manually enter it somehow (I assume that's possible, but time consuming).  I think EIT scanning works on the HDHomeRun, but not having one, I've obviously never tried it myself - if you're planning on going this route, you might do more reading to make sure.

> 
*(Although with the headache I've gotten from trying to find tuners/remotes, I'm concerned that using a DVD reader/burner on Linux is probably going to have it's own issues.)

Understandable that you'd be concerned, but I believe that DVD reading and burning has worked fine in Linux for many, many years.  Drives are pretty well standardized - tuners and remotes are not.  The problem that you might run into though, is barely the fault of Linux: copy protection on newer DVDs can make playing, and especially ripping, new releases problematic.  

[INDENT]   Marc[/INDENT]



Here is a list of currently supported ***_MCE remote hardware_*** from lirc_mceusb2.c  ... the only caveat is that sometimes the vendors - especially cheap ones - will change something on their own, and break compatibility with existing drivers (this is a problem for both Windows and Linux).  The list of supported MCE remotes is much larger because multiple remotes will be based upon the same hardware - just with a different name on the plastic:
```
static struct usb_device_id usb_remote_table [] = {
  139 	/* Philips eHome Infrared Transceiver */
  141 	/* Philips Infrared Transceiver - HP branded */
  143 	/* Philips SRM5100 */
  145 	/* Philips Infrared Transceiver - Omaura */
  147 	/* Philips Infrared Transceiver - Spinel plus */
  149 	/* SMK/Toshiba G83C0004D410 */
  151 	/* SMK eHome Infrared Transceiver (Sony VAIO) */
  153 	/* SMK bundled with Hauppauge PVR-150 */
  155 	/* Tatung eHome Infrared Transceiver */
  157 	/* Shuttle eHome Infrared Transceiver */
  161 	/* Gateway eHome Infrared Transceiver */
  163 	/* Mitsumi */
  165 	/* Topseed eHome Infrared Transceiver */
  167 	/* Topseed HP eHome Infrared Transceiver */
  173 	/* Ricavision internal Infrared Transceiver */
  175 	/* Itron ione Libra Q-11 */
  177 	/* FIC eHome Infrared Transceiver */
  179 	/* LG eHome Infrared Transceiver */
  181 	/* Microsoft MCE Infrared Transceiver */
  183 	/* Formosa eHome Infrared Transceiver */
  185 	/* Formosa21 / eHome Infrared Receiver */
  187 	/* Formosa aim / Trust MCE Infrared Receiver */
  189 	/* Formosa Industrial Computing / Beanbag Emulation Device */
  191 	/* Fintek eHome Infrared Transceiver */
  193 	/* Pinnacle Remote Kit */
  195 	/* Elitegroup Computer Systems IR */

```

---

### Post by uopjohnson on 2008-10-22
While the mythtv project has come a long way and mythbuntu in particular is nearly flawless you shouldn't jump into a PCR project unless you are willing to get your hands dirty.  There are a lot of new technologies to learn.  
All that aside, I just did an HDHomeRun install and I couldn't be happier.  It worked perfectly 'out of the box'.  I personally use a streamzap remote I got from amazon, it comes with an IR reciever and is supported well in mythbuntu.

---

### Post by R3M3 on 2008-11-02
The HDHomeRun looks like a great unit. Unfortunately, I'm hoping to be able to capturing from analog as well. (The HDHomeRun is digital only.)

That said, I think I've found an answer. From what I can tell, Intrepid Ibex (Ubuntu 8.10) should have full support for the Hauppauge HVR-1950, which supports both (U.S.A.) analog and digital. As I understand it, it even comes with a functional remote. Documentation for use on Linux is a little spotty, so I may have to get a little dirty, but hopefully I won't be jumping off a cliff.

---

