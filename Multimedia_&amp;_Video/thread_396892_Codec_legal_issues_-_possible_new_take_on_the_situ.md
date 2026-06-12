---
title: "Codec legal issues - possible new take on the situation..."
date: 2007-03-30
forum: Multimedia &amp; Video
---

### Post by Jim March on 2007-03-30
Folks,

I'm going to start with libdvdcss but then I have questions regarding MP3 codecs below.

As y'all probably know, it's illegal in the US to use software that circumvents copy protection.  But does libdvdcss **on it's own** do that?

Background: I'm about ready to start installing Feisty for others once it's out of beta and I need to be legal.  Short form, I'm an American political activist who deals with some fairly hairy stuff...google my name with the word "Diebold" if you're interested.  So I need to stay legit.

What I'm thinking (and have been researching) is this: libdvdcss is not itself able to circumvent copy protection.  It's able to circumvent region codes in order to read basically anything, and all players that use libdvdcss can thus dodge region codes.

But that alone doesn't get you in hot water under the DMCA (USofA ultra-nasty copyright enforcement law for you furriners :)).

Some DVD players can also act as rippers - VLC for starters.  So VLC isn't legal in the US.  But on my machine (Feisty beta) I not only don't have VLC, I don't have any rippers whatsoever.

So is libdvdcss on my system, the way I'm configured now, legal?  It appears to me it IS.  Any feedback or info on this appreciated.

---

MP3 Help Needed:

Fluendo claims to have a legal, licensed MP3 binary codec available, and this binary allegedly works with Banshee.  See also:

[http://www.fluendo.com/resources/fluendo_mp3.php](http://www.fluendo.com/resources/fluendo_mp3.php)

I want to try it out.  Problem: I tried to play MP3s already and Feisty's auto-codec-installer installed...something.  Dunno exactly what, but MP3s play now.  Does anybody know what MP3 codec got auto-installed, and where it got put?  I want to nuke it, confirm that MP3 playback is broke, and then install Fluendo's critter to try it.  Any help finding and nuking my existing codec highly appreciated.

Next: what else is legally squirrelly?  MPEGs?  WMVs?  What else is of concern?

I can't be the only one looking to re-distribute (properly, pursuant to GPL and all) Ubuntu in the US and concerned about legalities.

---

### Post by zorkerz on 2007-03-30
Im very interested in all of this as well.  I know virtually nothing about how it all works but would like at the least to know the legality of all the codecs and programs i use. I wonder if a section could be added to the wiki or somewhere appropriate that has the legality of packages in specific regions all laid out.

As for your mp3 support. How did you go about using/starting feisty's auto-codec installer im using feisty but had mp3 support before i upgraded so I have not seen this method for installing codecs.

I hope a dialog can be kept up about this somewhere

---

### Post by Jim March on 2007-03-30
If you have a clean install of Feisty and you go to call an MP3 file, the player app will of course error out.  A new Ubuntu app will pop up and basically go "hey, I can help with that" and if you agree, load...well SOMETHING :).  Not quite sure what it's loading (or where) is the issue.

Also: I didn't know until I checked that VLC could rip.  Whoops.  Got rid of it and fortunately MPlayer still dealt with commercial DVDs no problem...but I had separately loaded (compiled from source actually) libdvdcss before loading VLC.  So that might be necessary.

Can GXine rip?  For that matter can MPlayer with some trickery?  Because if I'm right, the key to legal use of libdvdcss is "don't have a ripper around".

Just like owners of an AR15 rifle better not have a full-auto sear anywhere nearby, or you've got a "machine gun" even if you haven't connected the two.  You can buy full-auto sears at a gun shop but you'd damned well better have either no gun it can fit, or a legally-owned with massive paperwork (made prior to 1986) full-auto M16 rifle in which case the full-auto sear is a legally owned spare part.

What I'm saying is, situations where you can own one thing, or the other, but not BOTH do happen.  The above with rifle parts is one example I've read about.  I think libdvdcss and rippers are in basically the same boat (with a LOT less penalties and no stormtroopers ready to kick your cat to death if they think you're hinky thank God)...

---

### Post by zorkerz on 2007-03-30
Check this out [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) it just might be what you are looking for. I wish the add/remove applications was more informative on what it is actually installing. There should at least be a reference page somewhere.

So if any program can be used as a ripper you must get ride of them in the us at least to maintain legality if you have libdvdcss? Or is any ripper that bypasses copy protection in general illegal? 

How about audio cds they don't have copy protection (i believe) so it would be fine to have a ripper for this?

---

### Post by merlyn on 2007-03-30
> **Jim March said:**
> I want to try it out.  Problem: I tried to play MP3s already and Feisty's auto-codec-installer installed...something.  Dunno exactly what, but MP3s play now.  Does anybody know what MP3 codec got auto-installed, and where it got put?  I want to nuke it, confirm that MP3 playback is broke, and then install Fluendo's critter to try it.  Any help finding and nuking my existing codec highly appreciated.

Run synaptic and do a search with 'description and name' enabled for mp3 and again for fluendo. If a green square appears next to the packages that are installed.

Fluendo's Mp3 codec is in "Universe", I'm not sure at all about the legal standing of packages in this repository in the US. But it could be a starting point for further research.

Cheers.

---

### Post by Jim March on 2007-03-30
Merlyn: well that was good info, but not quite enough :).

Searching by "MP3" (tried upper and lower case) produces a whole lot of stuff checked, but I can't tell which one is the likely codec Banshee for example is using.

Searching Fluendo, it's clear that IS in the Ubuntu repositories...but not turned on.

So, if Fluendo is legal while another isn't, whatever Feisty stuck in there to meet my MP3 needs is NOT the legal one (Fluendo)!?

See, now things are getting downright weird.

So again: can anybody tell me which MP3 codec Banshee is likely using right this second?  Is there a way to query Banshee for it?

---

### Post by merlyn on 2007-03-30
You could check [this]("https://help.ubuntu.com/community/RestrictedFormats") link out and see if you have any of the codecs mentioned installed.

I would imagine that as these are listed as restricted you would be best to uninstall them if you have them that is.

Also drop on over to the banshee [forums]("http://banshee-project.org/forums/").

I had a quick squiz and it turns out to be a member of the gstreamer family.

That being the case do a search in synaptic for gstreamer, this time do the search with "name" only to isolate those codec packages.

You might also check out the [gstreamer]("http://gstreamer.freedesktop.org/") site, that would be most likely the best place to check on the legal issue of any of their codecs in relation to the US.

Or then again [here's]("http://www.fluendo.com/press/releases/PR-2005-05.html") an announcement regarding the fluendo mp3 codec with even more links, including an info email link.

[Here]("http://www.ubuntu.com/community/ubuntustory/components") is some really good info on the scope of the different repositories in Ubuntu and there relationship to the free software policy.

Google is your friend.

Cheers mate.

---

### Post by Animortis on 2007-03-30
I also use Ubuntu for business related purposes where absolute legality is necessary. To find that Feisty will willingly install things that will put me in legal hot water without considering the consequences to U.S. users seems highly irresponsible.

I am currently using Edgy with no MP3 codec installed - I have RealPlayer installed for that as it is, and it is very bad at playing MP3s (lot of skipping). I was hoping Feisty had figured out a way to get me to be able to safely use MP3s and WMVs on my computer but I fear that has not only not happened, but Feisty will throw an illegal hot-potato at me by actively installing things that could jeopardize the legality of me using Ubuntu instead of Windows for my productivity work.

I guess I should finish with a question:

If I use Feisty and click a WMV file or MP3 file and codec-installer pops up and offers to install the codec for me, will I be breaking American law by clicking "Okay?"

---

### Post by LuisC-SM on 2007-03-30
Taken from: [http://en.wikipedia.org/wiki/Libdvdcss](http://en.wikipedia.org/wiki/Libdvdcss)

    [I]"The correct title of this article is libdvdcss. The initial letter is shown capitalized due to technical restrictions.

libdvdcss is a free, highly portable library for accessing and unscrambling DVDs encrypted with the CSS system. It is part of the VideoLAN project and is used by VLC and all other free/open source DVD players such as Ogle, xine-based players and MPlayer.

libdvdcss is designed to be platform independent, with versions for GNU/Linux, Microsoft Windows, Mac OS X, BeOS, BSD and Solaris. It is released under the GNU GPL.

libdvdcss is not to be confused with DeCSS. While DeCSS uses a cracked DVD player key to perform authentication, libdvdcss uses a generated list of possible player keys. If none of them work (for instance, when the DVD drive enforces region coding) a brute force algorithm is tried so the region code of a DVD is ignored. [COLOR="Red"]**Unlike DeCSS, libdvdcss has never been fought over in a courtroom.**[/COLOR]

[COLOR="DarkRed"]In many countries it is forbidden to sell or document programs that provide ways around copy prevention systems. **CSS is not a copy prevention system**, but rather primarily a region-control market segmentation system.[citation needed] Despite this fact, many Linux distributions do not contain libdvdcss (for example Debian, SUSE Linux, and Ubuntu) due to fears of running afoul of DMCA-style laws. In most of these cases, the library can be easily downloaded from the Internet. In other cases some distributions refrain from preloading libdvdcss onto their install discs but it is available in their software repositories.[/COLOR]"[/I]

I think that if you r going to use it JUST to WATCH DVDs, I see nothing to worry about, the problem starts when you install a ripper, then you are violating the law IMHO.

Regards

Luis C. Suárez

EDIT: I missed some comments.

[I]This article says that css is not copy protection, but the copy protection article says it is. Is this a contradiction?

    As I understand it, CSS does not prevent a bit-for-bit copy of a DVD from being played, so it does not act as a copy protection system. All it enforces is the need for a player to have access to the necessary keys to unscramble the content on the DVD. Other systems, such as SCMS or Blu-Ray actively attempt to prevent copies being made of the data. Note that this subject is a legal minefield, with laws differing from country to country, so please don't assume that anything said here gives you licence to do anything in your jurisdiction. WLD 16:40, 6 August 2006 (UTC)

Danieleran 22:06, 29 March 2007 (UTC) It is silly to say that CSS isn't copy protection because you "can still copy the encrypted bits." You quite obviously can't copy them in a useful way unless you decrypt it first. It's only ever the content that's being encrypted, not the ability to read bits on the disc; that's why its the Content Scrambling System. Suggesting that CSS is only a 'region enforcement' is disingenious and misleading, and only makes the arguement for fair use sound ignorant. It most certainly offers no legal protection, and suggesting that laws are lacking in some areas doesn't help or inform either.[/I]

---

### Post by tom56 on 2007-04-10
> **Animortis said:**
> If I use Feisty and click a WMV file or MP3 file and codec-installer pops up and offers to install the codec for me, will I be breaking American law by clicking "Okay?"

Not criminal law, but civil law yes. The mp3 format is patented and you have to pay a license fee to use it. On Windows PCs this fee is paid for you by whoever supplies your mp3 player software. On Ubuntu the fee is not paid for you so you are potentially violating patent law.

Fluendo is completely legal because they have paid the license fee.

---

### Post by darrenm on 2007-04-10
I believe the package that Ubuntu installs to play MP3's is gstreamer0.10-plugins-ugly

I'm sure I remember it detailing the legality issues before you agree to install it though.

Even though I don't live in the US I completely disagree with software patents so I only use OGG, PNG etc which are open and patent free.

---

### Post by az on 2007-04-10
I think the problem with dvd decryption is not the legality of the software, but the patent on decrypting dvds.  Even if the software that you use is perfectly legal (in terms of obtaining it and using it according to the author's terms of use) it violates the patent on dvd encryption.  That is the licence you need to buy to legally read encrypted dvds on any device.

> **tom56 said:**
> Not criminal law, but civil law yes. The mp3 format is patented and you have to pay a license fee to use it. On Windows PCs this fee is paid for you by whoever supplies your mp3 player software. On Ubuntu the fee is not paid for you so you are potentially violating patent law.

Fluendo is completely legal because they have paid the license fee.

The end-user does not have to pay a royalty to use MP3.  That is specified.  What is required is for the distributer of the software to pay for the priviledge of providing mp3 support out-of-the-box.

The way Ubuntu does it is that the end-user installs the mp3 codec themself.  So long as the end-user does not redistribute the codec or use it for commercial use, you are not required to pay the royalty.  So long as Ubuntu does not ship the codec along with the install cd, they don't have to pay the royalty.

I wish I had a link for you, but it is on the mp3 patent royaly pricelist.

Also, apparently, CNR (linspire) will provide an easy way for Ubuntu users to pay for and obtain the required licences through their service.  So you will be able to pay for the packages and run them without any legal worries.

---

### Post by tom56 on 2007-04-10
[QUOTE=az]The end-user does not have to pay a royalty to use MP3.  That is specified.  What is required is for the distributer of the software to pay for the priviledge of providing mp3 support out-of-the-box.

The way Ubuntu does it is that the end-user installs the mp3 codec themself.  So long as the end-user does not redistribute the codec or use it for commercial use, you are not required to pay the royalty.  So long as Ubuntu does not ship the codec along with the install cd, they don't have to pay the royalty.[/QUOTE]

I stand corrected regarding license payments: I think you are right that you only have to pay to distribute it - not to use it.

However I don't think that not installing by default would be considered a loophole because by hosting it on their servers Canonical/Ubuntu are still distributing it.

---

### Post by golem3 on 2007-04-10
Is there a lawyer here specializing in intellectual property and/or patent law that can shed some light on this issue here in the USA?

---

### Post by zorkerz on 2007-04-10
Yes this is an issue that really needs some looking into by lawyers. At some point once the issues have been cleared up I think there should be a permanent page for this. Im not sure if it is appropriate for the wiki or any official ubuntu site to have this information for all jurisdictions but is sure seems to me that it needs to be accessibly somewhere.

---

### Post by LuisC-SM on 2007-04-10
> **tom56 said:**
> Not criminal law, but civil law yes. The mp3 format is patented and you have to pay a license fee to use it................
Fluendo is completely legal because they have paid the license fee.

Well well well, I really believe you r a BIG lawyer, aint'cha?.... 
>>>criminal law ...?????<<< (What's this suppost to mean??)
>>> civil law...??? <<< (CIVIL????? OH MY GODDDDD) 
I'm NOT (by far) a lawyer, but to my knowledge (I'm mexican BTW), civil laws only applyies to citizens in one city or state. FEDERAL law applies to the whole country and could or might have been extended to more than one country.... said that......!!!
>>>Fluendo is completely legal because..........<<<< YES You ARE Just Right!!!!!!!
Please, don't take me like I'm trying to teach u any kind of legal sh_t... I believe that everyone who's been answering this thread knows very well  about MP3's pattent and Copyrights... is it legal to use Fluendo in USA????..... if Yes..... wihich law am I breaking???
I'd like to have a USA attorney to answear this....
In the other hand, (to the original poster) use Click -n Run (from [www.linspire.com](www.linspire.com)) as a repository source to have everything legal (assuming u will install any ubuntu flavor).  ... [http://info.linspire.com/comments.html](http://info.linspire.com/comments.html) (not sure if is the right link :()

Kind Regards

Luis C. Suárez

---

### Post by tom56 on 2007-04-12
> **LuisC-SM said:**
> 
>>>criminal law ...?????<<< (What's this suppost to mean??)
>>> civil law...??? <<< (CIVIL????? OH MY GODDDDD) 

Criminal law is something you can go to prison for. Civil law is something you can be sued for. Civil law is also sometime called tort, but tort is just one area of civil law. You might find the following helpful...

[http://en.wikipedia.org/wiki/Civil_law_%28common_law%29](http://en.wikipedia.org/wiki/Civil_law_%28common_law%29)
[http://en.wikipedia.org/wiki/Criminal_law](http://en.wikipedia.org/wiki/Criminal_law)
[http://en.wikipedia.org/wiki/Politeness](http://en.wikipedia.org/wiki/Politeness)

Technically infringing on a patent is against criminal law in the U.S. and Europe, but as no-one is sure who owns the "most" genune mp3 patent the police won't come knocking at your door. However patent owners could sue (civil law), because aside from anything else - the burden of proof is lesser in civil law. (Balance of probablities vs. reasonable doubt). That last bit probably only applies to the UK though.

---

### Post by rsambuca on 2007-04-12
Here is a link to some [[COLOR="Red"]mp3 royalty rates.[/COLOR]]("http://mp3licensing.com/royalty/software.html")

My understanding is that basically, if you are ripping a commercial DVD, you are in violation of the DMCA.

---

### Post by LuisC-SM on 2007-04-13
Thanks for opening my horizons (I really mean it).

As fas as I know, and as posted earliear, I'm not by any meanings a lawyer. 

Every time you "brake", "violate" or "infringe" the law (no matter which one) you are commiting a "**[COLOR="DarkRed"]criminal act[/COLOR]**". No matter the nature of the law. And, naturally, you can be sued by that. 

Regards

Luis

Edit: I had heard all the time "Penal Law" Iin wikipedia they state as the same, so forgive my ignorance and acept my appologies.

---

