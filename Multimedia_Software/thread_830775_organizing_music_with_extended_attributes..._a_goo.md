---
title: "organizing music with extended attributes... a good idea?"
date: 2008-06-16
forum: Multimedia Software
---

### Post by mokapot on 2008-06-16
hi! i'm new, be kind plz! (=

so, i'm looking for a nice solution to how to best put metadata to use for my music collection. i like having a structured way of adding metadata to files instead of constructing long an unwieldy filenames and i don't particularly fancy the built-in metadata fields in the different file formats. (i'm looking for a more general solution that can be used for all types of files.)

i'd like to use something that goes beyond that and is well integrated into the filesystem. i figured: *"oi, [extended attributes](http://en.wikipedia.org/wiki/Extended_file_attributes#Linux) should do the trick!"* so, i signed up here cause i've found a lot of good information on here in the past.

the problems that i came to think of after a bit of googling is: 1) those extended attributes should be visible in the file browser. so, what file browsers support extended attributes on linux?

2) is search as fast as if i'd be searching for say a substring in a filename? i guess i wonder how well ext3 handles these attributes.

3) which audio players can handle this type of extra information? would i be able to customize which extended attributes that would show up in the playlist?

anyone who has any thoughts and/or experience on this topic, please share your thoughts! how do you organize your music collection? 

\\:D/ 

-mokapot

---

### Post by mozetti on 2008-06-16
I don't think you're going to find many (any) audio players that will use extended attributes for organizing music, other than using the id3 tags. I'm assuming you were talking about id3 tags in your statement that you: > don't particularly fancy the built-in metadata fields in the different file formats.

id3 tags were added specifically for this kind of data, so the audio players use them to organize the audio files. There's really no reason for programmers to add the ability to use extended attributes other than id3 tags. They already have the organization function using id3 tags, so it would be redundant. And for most people, if they want to have that info, then they use id3 tags.

---

### Post by mokapot on 2008-06-16
hi mozetti! thanks for giving your thoughts on this matter!

> **mozetti said:**
> I'm assuming you were talking about id3 tags in your statement that you: 



yes, that's correct.

> **mozetti said:**
> id3 tags were added specifically for this kind of data, so the audio players use them to organize the audio files. There's really no reason for programmers to add the ability to use extended attributes other than id3 tags. They already have the organization function using id3 tags, so it would be redundant. And for most people, if they want to have that info, then they use id3 tags.

yes, what you say is true. most people don't care and those tags work alright. now, i like going about things in a more general way. some friendly coders added extended attibutes support to the fs and i'd like to make them happy by using it if that's possible. :> 

there's a lot of other types of media that doesn't have built-in support of metadata and i'd like to make use of this in other ways as well. i've been missing a good way to annotate files in windows. also, i think it's not that elegant a solution. (i'm pretty anal i guess :))

-mokapot

---

### Post by mokapot on 2008-06-17
bump!

any takers? damn, a lot of traffic on this site!

-mokapot

---

