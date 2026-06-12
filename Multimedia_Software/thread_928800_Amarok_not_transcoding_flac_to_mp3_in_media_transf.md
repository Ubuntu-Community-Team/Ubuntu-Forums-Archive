---
title: "Amarok not transcoding flac to mp3 in media transfer"
date: 2008-09-24
forum: Multimedia Software
---

### Post by AusIV4 on 2008-09-24
I've been managing my iPod with Amarok for quite some time. Several months back I upgraded from Dapper to Gutsy, giving me Amarok 1.4.8. Today was the first time I've tried to transfer flac files since upgrading. Previously I used transKode, but I had some issues getting it to work on my new 64 bit platform, so I opted for AmaKode instead. I've run the script and configured it to transcode to mp3 when necessary, but when I try to transfer my FLAC files, I end up with FLAC files on the iPod, rather than mp3s.

I'm having a hard time figuring out whether amakode is failing to transcode, or if Amarok is never giving it the signal to transcode. Does anyone have any tips?

Thanks for any help.

---

### Post by AusIV4 on 2008-09-28
Changing the option from "Transcode when necessary" to "Transcode when possible" seems to have fixed the problem, but it's not an optimal solution, because I sometimes have m4a's to transfer to my iPod, and I don't want it to transcode those. Is there any way to convince Amarok that it's necessary to transcode FLAC before putting it on the iPod?

---

### Post by shayguitarra on 2009-02-07
I'm having the same problem. I'm using "transkode". I have about half of my music in flac and half in mp3. When I select 'transcode when necessary' it just transfers my flac files straight to the ipod. However when I try to transfer a wma file with this option selected it does convert it. So it seems that (for me anyway) the only problem is with flac files.

'Transcode whenever possible' on the other hand just converts everything including mp3 and m4a's.

It seems that Amarok thinks the ipod supports flac files. And unlike with MTP players there is no way to give an ipod (selected as such) a list of supported files.

If someone else has had this problem how did you solve it, or else can anybody suggest a way to solve it?

I'm using Amarok 1.4.10 on Intrepid. But I had the same problem on Hardy.

---

### Post by shayguitarra on 2009-02-08
OK, I seem to have stumbled upon a work-around of sorts for this. So I'll put it up in case someone has the same problem in the future.

This is what I'm doing for smart playlists, it should be even more straightforward for manual playlists.

Say you have a playlist called 5 Star, containing all of your favourite tracks. This will obviously include all of your 5 Star tracks, regardless of file type. So you need to split it, so that one playlist has ipod compatible files and the other doesn't. However you will then realise, as I did that Amarok (incredibly enough) does not allow you to filter by 'Type' when creating a smart playlist. It will however allow you to filter by bitrate. So in the case of flac (or other lossless formats) you just set the bitrate as above 320. This will leave you with all of the flac files in your playlist. You can then transfer them with the 'transcode whenever possible'.

Then re-edit the playlist to include bitrate below 321 (so you include any mp3 files with a bitrate of 320kbps). Transfer with 'transcode when necessary'. Please note your two playlists will need to have different names otherwise (as I found out) you will just delete the files you previously put on your ipod (so 5Star FLAC and 5Star MP3 etc.). When this is done, remove the bitrate filter from your playlist, restoring all files and simply transfer it. As all of the files already exist on the ipod there is no converting or overwriting to be done. Delete your two filtered playlists and there you have it.

One problem with this method arises if you have incompatible files in a lossy format (e.g. wma) in which case the bitrate filter won't work. As I have only about a dozen or so wma files I simply dragged and dropped them into the transfer list and left them included in the 5Star MP3 playlist. I suppose you could also just include the file type in your comment box and filter this way if you have a large amount.

Anyway, this might be an incredibly obvious solution but I just thought I'd post it so this topic can be marked as (sort of) solved. And it might save someone some gnashing of teeth in the future. :)

---

