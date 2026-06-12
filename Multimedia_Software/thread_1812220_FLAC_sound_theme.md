---
title: "FLAC sound theme???"
date: 2011-07-26
forum: Multimedia Software
---

### Post by firefish5000 on 2011-07-26
I would like to know if there is any way (via terminal or gediting a file) to use .flac files instead of .ogg in a sound theme file?

I am creating a sound theme (several truthfully) and I would like to use the FLAC format if possible. Thanks.
Ubuntu version 11.04

---

### Post by firefish5000 on 2011-07-28
*Bump (though I'm not sure what that means)
I have been looking through several files (and read several hundred lines of code) and have not yet found the answer. I't not a question of is it possible, but how to do (its Ubuntu, worst case scenario its extremely difficult to do)

---

### Post by firefish5000 on 2011-07-29
After searching some more, I found that freedesktop mentiond a psudocode
```
The exact algorithm (in pseudocode) for looking up a sound in a theme is:

FindSound(sound, locale, outputprofile, theme) {
  filename = LookupSound (sound, locale, outputprofile, theme)
  if filename != none
    return filename

  if theme has parents
    for parent in theme.parents {
      filename = LookupSound (sound, locale, outputprofile, parent)
      if filename != none
        return filename
    }

  return none
}
     
With the following helper functions:

LookupSound (requestedname, requestedlocale, requestedoutputprofile, requestedtheme) {
  for theme in (requestedtheme,
                "freedesktop",
                "") {
    for profile in (requestedoutputprofile, "stereo", "") {
      for each subdir in $(theme subdir list) {
        if DirectoryMatchesOutputProfile(subdir, profile) {
          for each directory in $(basename list) {
            for each name in (requestedname,
                              truncatesuffix(requestedname, "-"),
                              truncatesuffix(truncatesuffix(requestedname, "-"), "-"),
                              truncatesuffix(truncatesuffix(truncatesuffix(requestedname, "-"), "-"), "-"),
                              ...) {
              for each locale in (requestedlocale,
                                  truncatesuffix(requestedlocale, "@"),
                                  truncatesuffix(requestedlocale, "_"),
                                  "C",
                                  "") {
                for extension in ([COLOR="Red"]"disabled", "oga", "ogg", "wav"[/COLOR]) {
	          filename = directory/theme/subdir/locale/name.extension
                  if exist filename
                    return filename
                }
              }
            }
          }
        }
      }
    }
  }

  return none
}

DirectoryMatchesOutputProfile(subdir, profile) {
  read OutputProfile from subdir
  if OutputProfile == profile
    return true
  return false
}
```
Im not going to say that my answer is editing the code there, because frankly I have no clue. But I believe that there might be a small chance that adding FLAC would help. But I am clueless as to what the code is, where it is located(this would be more helpfull than what it is, but I could search for it via regexxer if I knew. but then again I am not sure if its a compiled code or not...)
If anyone could provide me with a little guidance (your going the wrong way, that wont do anything I already tried, this can easily be solved with ___) it would be greatly appreciated.

p.s. I have also found some sound theme managers, but I cant get them to work.

---

### Post by .... on 2011-07-30
It would be far easier to convert your files into high quality .ogg since libcanberra wants ogg. I doubt you or your target audience would be able to tell the difference in a double blind listening test unless they have really high quality audio equipment (and even then..).

---

### Post by firefish5000 on 2011-07-31
hehehe, I feel real dumb for an obvious reason (i didnt read the title of the page i got that previous code from, libcanberra 0.28)
I'll take your advice on converting them to a compatible type, (my current computer dose not have the best audio equipment) but I am still going to mess with the code(got to have fun)
As for my intended audience, its a large anime community. On the other hand, no more than a droplet will probably download this and i doubt more than 10 would be willing to modify their libcanberra package. (im one of the 10, i need some more experience doing this anyways.)
Thanks for your help

---

### Post by firefish5000 on 2011-08-02
Converted to WAV successfully for all but 1 file (no clue why, Gnac closes every time i try this one instantly, if I am converting 100 before it it will still close the second i push the button)
I forgot what else I was going to type here, I am pretty sure I had a good reason to come back but oh well.

---

