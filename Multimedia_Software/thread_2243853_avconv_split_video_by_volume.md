---
title: "avconv split video by volume"
date: 2014-09-11
forum: Multimedia Software
---

### Post by drummingpariah on 2014-09-11
I'm still in the planning stages of writing this tool, but I have ~20minute video **files** of motorsport footage that I would like to break apart into ~30-second **clips** and remove 'dead footage'. The clips are from a camera placed in a fixed location, set to 'record' then a race car whizzing by every 2 minutes or so. As you might imagine, going through all of those **clips** (10 cameras and 10 sessions means ~100 **clips** to split apart) is a tedious process.

I don't have enough familiarity with the ffmpeg/avconv tool to know how to identify these sections well enough, so I see a few different methods of approach:
[LIST=1]
[*]Use motion detection to identify 'interesting' sections, and add a buffer to each then copying each out to a specific file. This would capture all the 'interesting' parts of the **file**, and the **clips** could then be sorted (by hand, as I don't see an easier way) by car number.
[*]Use audio to identify 'interesting' parts of each **file**. I would prefer this, as it gives me everything I want with nothing I don't. I could identify 'interesting' parts as any section with audio louder than a preset threshold.
[/LIST]

The actual export is relatively simple:
```

for clip in $videofile:
do
    avconv -ss $clipstart -t $clipstart-$clipend -i $videofile.mp4 -codec copy $clip.mp4
done
```

What I'd really like help with is identifying where to start the clip and where to end it. I'm just putting the logic together in bash, as that's where I have the most experience.

Can anyone help with this logic? I feel like I'm missing an obvious step, but apparently need to see an example of one approach to this in order to solve it.

---

