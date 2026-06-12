---
title: "Execute script over ssh via Windows &amp; Putty"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by breaksyid on 2009-04-07
Hi. I'm setting up a media centre which I want to be able to rip DVD's to ISO's on. I don't want to interrupt the media UI while doing this, so I wrote a little bash script with the hope of being able to ssh in via putty on my laptop (or terminal on my iPod Touch) and executing it. However, when I run the script, nothing happens. Is it possible to do this? This is the script (my first ever so excuse the lack of exception handling):

```
read -p "Enter name of the movie: " MOVIE_NAME
read -p "Enter the path you want to save to: " PATH_TO_SAVE

echo "Right. Let's give this a go then shall we. If you don't see any errors, it's still working fine."

if [ ! -d "${PATH_TO_SAVE}" ]; then
  mkdir "${PATH_TO_SAVE}"
fi

if [ -d "${PATH_TO_SAVE}" ]; then
  sudo dd if=/dev/scd0 of="${PATH_TO_SAVE}${MOVIE_NAME}".iso
fi

echo "--------------------------------------------------------"
echo "If there are no error's above, all went well. Let's just pop that DVD out for you."

eject
```

---

