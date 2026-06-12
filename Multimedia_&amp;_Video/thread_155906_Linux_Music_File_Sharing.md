---
title: "Linux Music File Sharing"
date: 2006-04-06
forum: Multimedia &amp; Video
---

### Post by dolson on 2006-04-06
Hello all.

On the LAU list, it was brought up to create a central resource for file-sharing various Linux-related music files (not songs!), such as presets, synth patches, etc.

So, I'm going to be working on such a site with a couple other people.

Here is the current list of filetypes that I want to support on this site, but I am asking for you to review it, as I likely missed many types of files we want to support:

- Audio Samples (*.wav, *.ogg, *.mp3, *.au, *.aiff)
- Gigasampler Banks (*.gig)
- SoundFonts (*.sf2)
- MIDI Samples (*.mid, *.smf)
- Seq24 Loops (*.s24)
- JSynthLib Patches (*.patchlib)
- SysEx Files (*.syx)
- Hydrogen Kits and Beats (*.h2drumkit, *.h2song)
- ZynAddSubFX Settings (*.xiz, *.xmz, *.xpz)
- JAMin Templates (*.jam)
- QjackCtl Patchbays (*.xml)
- JACK-Rack Racks (*.rack)
- AlsaModularSynth Patches (*.ams)
- amSynth Patches (*.amSynthPreset)
- QMidiArp Arpeggios (*.qma)
- QMidiRoute Routes (*.qmr)
- Om Patches (*.om)
- Pd Patches (*.pd, *.pat)

I know that the usefulness may be questionable for some of these, but I don't want to exclude something just because a few people won't use it. But if, for example, everyone agrees that QjackCtl or JAMin files are useless to share, then we can remove them.

Also, my goal is that all files uploaded can be used for any purpose, short of someone collecting them and selling them... So you could take any samples or loops I upload and use them in any way you like, to create songs of your own for your new hit album, or to modify them and remix them and send them back to the site for everyone else to share. Is there anyone who disagrees with such a disclaimer/license for the site
content? Obviously you can't upload work that someone else did under a restricted license, so we won't see the Titanic SoundFont uploaded or something like that.

Is there any particular feature you would want on the site that we might not have already though of? We do not want articles posted there, nor a wiki, or anything like that. This will be strictly a file-swap site, but features to make it funner/easier/better/unique would be welcome suggestions (no promises that we can or will implement anything).

Thanks in advance for any feedback. Feel free to email me direct if you prefer.

Also, if anyone is interested in being staff on the site, please let me know. Basically, at this time, the only thing a staff member will do is check uploads and flag anything that is malicious so it is hidden. If you don't want to commit to it, then don't volunteer. We will do our best to filter out that kind of crud without human intervention, but it may be necessary anyhow.

---

### Post by rytmisk on 2006-04-10
A very good initiative!! Is that what you're working on at the moment since I have not seen any changes at ubuntustudio.com for over a week?

I really appreciate your efforts! Ubuntu is the best choice for me in all other respects than audio at the moment, and with ubuntustudio - well I am saved:-)

But I really think there are a few apps that are necessary: fst, dssi and rosegarden 1.2.3 are still missing. Someone build ubuntu debs for these please!!!!

Best regards
Ketil

---

### Post by eriefisher on 2006-04-10
[QUOTE=dolson]

Also, my goal is that all files uploaded can be used for any purpose, short of someone collecting them and selling them... So you could take any samples or loops I upload and use them in any way you like, to create songs of your own for your new hit album, or to modify them and remix them and send them back to the site for everyone else to share. Is there anyone who disagrees with such a disclaimer/license for the site
content? Obviously you can't upload work that someone else did under a restricted license, so we won't see the Titanic SoundFont uploaded or something like that.[/QUOTE]

This sounds like the Creative Commons Licence

---

### Post by dolson on 2006-04-10
[QUOTE=rytmisk]A very good initiative!! Is that what you're working on at the moment since I have not seen any changes at ubuntustudio.com for over a week?

I really appreciate your efforts! Ubuntu is the best choice for me in all other respects than audio at the moment, and with ubuntustudio - well I am saved:-)

But I really think there are a few apps that are necessary: fst, dssi and rosegarden 1.2.3 are still missing. Someone build ubuntu debs for these please!!!!

Best regards
Ketil[/QUOTE]
I am not working on it yet, other than brainstorming ideas and features. I haven't had tons of feedback yet, so I'm not going to rush it. Plus I want it to be done right.

I am not the only person who can edit the wiki. I don't know every single thing about Linux audio, which is why this project IS a wiki... Although I have put about 95% or maybe more of the current content there, I don't have anything else to say right now. I don't have time to write up tutorials for all the apps I use at the moment, because I am working on another project at the same time. I will add new stuff there when I can. Otherwise, feel free to contribute.

Also, FST is not likely going to happen due to the VST SDK license. Until debian figures out a way to, and does accept it, then I don't see it happening for Ubuntu.

DSSI is already in debian and is supposed to be included in Dapper, but hasn't hit the archive yet.

Rosegarden is not likely to happen until Dapper+1, given that no one has stepped up to work on it in debian or Ubuntu yet.

You know that you can build packages, right? It's not that hard, and the more help there is, the better it's going to get.

eriefisher, I was thinking that too. Someone on the mailing list insists for GPL.. But I don't think it's fair to require me to keep, nevermind distribute the entire source of my songs - every preset, every patch, every track in its raw form, etc. It's not exactly the best license for this sort of thing. I think the CCL is better.. I have to talk to the others involved in the project and give them feedback too, and see what they think.

---

### Post by GameGod on 2006-04-13
[QUOTE=dolson]
Rosegarden is not likely to happen until Dapper+1, given that no one has stepped up to work on it in debian or Ubuntu yet.
[/QUOTE]

Huh?
Do you mean that there's no Rosegarden package for Ubuntu?

Either I don't remember compiling it myself (and used checkinstall), or I just installed it from a repository in Breezy... hmmm

---

### Post by dolson on 2006-04-13
Rosegarden 1.2.3, I am referring to. Sorry about not being clear.

---

### Post by nct on 2006-04-14
[QUOTE=dolson]
Rosegarden is not likely to happen until Dapper+1, given that no one has stepped up to work on it in debian or Ubuntu yet.
[/QUOTE]

Well, I was thinking this until I found that site:
[http://vireo.org/debian/rosegarden4/binary/]("http://vireo.org/debian/rosegarden4/binary/")

But I haven't tested yet.

Steph

---

### Post by dolson on 2006-04-14
[QUOTE=nct]Well, I was thinking this until I found that site:
[http://vireo.org/debian/rosegarden4/binary/]("http://vireo.org/debian/rosegarden4/binary/")

But I haven't tested yet.

Steph[/QUOTE]
Doesn't make a difference, we're already past Feature Freeze for Dapper, so therefore, it likely will not happen. Unless someone opens a UVF exception request and has it approved.

---

