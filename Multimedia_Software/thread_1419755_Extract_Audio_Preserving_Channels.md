---
title: "Extract Audio Preserving Channels"
date: 2010-03-02
forum: Multimedia Software
---

### Post by Martin Marshalek on 2010-03-02
Right now I'm working on project for a Music Theory class where we are supplanting the music in a movie scene with music we compose. Rather than simply muting the movie and playing our sound file over it, which would also make the voices and dialogue inaudible, I posited that we separate the original track into dialogue and music, erase the original music, and replace it with our own. For this purpose, I have installed Handbrake (to get the video from the DVD), Audacity (to work with the audio), WinFF (for conversion back to DVD format), Bombono (to put the final product back on DVD), and Kino for any editing of the video. 

I haven't used Kino much yet, but is there a way with it to export the audio from the video? Will this preserve audio channels. Will ripping with handbrake preserve audio channels as well?

Thanks for the help, sorry about the length of the post but the more information the better for getting help.

---

### Post by mcduck on 2010-03-02
You'll have really hard time doing that, especially if you don't have a solid background in audio editing.

Movies don't have separate audio tracks for music and speech, they are all merged in to one and the same track so you'd have to do some clever filtering based on sound frequencies and the difference between center, left & right channels to separate the speech and music, and even then the result is not likely to be very good.

---

### Post by Martin Marshalek on 2010-03-02
I had found that some DVD's keep certain things in different channels though. I don't remember where exactly though, so I'm not 100% sure of it's validity. Also, I ready many guides on how to make a "karaoke version" of a song in Audacity by filtering out vocals, so I would assume the same process backwards would achieve the desired result.

---

### Post by mcduck on 2010-03-03
> **Martin Marshalek said:**
> I had found that some DVD's keep certain things in different channels though. I don't remember where exactly though, so I'm not 100% sure of it's validity. Also, I ready many guides on how to make a "karaoke version" of a song in Audacity by filtering out vocals, so I would assume the same process backwards would achieve the desired result.

Sure, DVD's have different audio channels, but they aren't separate music/speech/sound effect -channels, just the surround channels (left, right, center, surround left, surround right, LFE etc..).

Also there might be different speech languages, but they are not separate channels that would be mixed with a separate music track, but instead each different language soundtrack includes both the music and speech.

You can try to use the vocal filter in Audacity, it does exactly the same frequency/channel difference filtering I described (although automatic tools usually give even worse results than manual process does). As far as I remember the filter in Audacity doesn't work with surround sound, and doesn't have any option for leaving the speech and removing the music, so you'll have to just see how well it manages to remove the speech from the soundtrack, and then try to subtract the resulting data from the original file to get a speech-only version. In addition the vocal remover Audacity has is made for music, not movies, so it assumes that all human voice is panned perfectly in the center and doesn't move around like it might do on a movie soundtrack.

But like I said, you shouldn't expect very good results. Most musical instrument (and the rest of the sounds in soundtracks) also produce sounds that are in the same frequency range with human voice, so it's *really hard* to get good results separating music and human voice once they have already been mixed into same track. Most likely you'll end with a file that still has the original music in it, although quieter than the original, and the speech might be a bit weird in some places since the processing has toned down some of the frequencies that would actually belong to the speech.. Still, it might be good enough for your purposes (At least if you play your own music loud enough... ;))

---

