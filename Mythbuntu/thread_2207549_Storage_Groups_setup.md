---
title: "Storage Groups setup"
date: 2014-02-24
forum: Mythbuntu
---

### Post by philip7 on 2014-02-24
I've finally gotten around to buying an extra HDD and thought it might be a good idea to look at using Storage Groups instead of my previous approach.

Originally I had two HDD, I partitioned one drive and used one partition for Recordings and the other for everything else. The 2nd HDD was used just for Videos.

When I mounted the HDD they were mounted straight the the required directory, i.e. Recordings mounted to /var/lib/mythtv/recordings and videos to /var/lib/mythtv/videos.

I then had some script that would transcode recordings into videos for long term storage.

[B]Settings up Storage Groups?
[/B]First of all I wanted to understand how to setup the Storage groups, I've read through the documentation and just wanted to check. Essentially I need to mount the HDD's using a generic name i.e. /mnt/mythtv/d1 /mnt/mythtv/d2.

Then create subdirectories under both folders:

[LIST]
[*]/mnt/mythtv/d1/recordings
[*]/mnt/mythtv/d1/videos
[*]/mnt/mythtv/d2/recordings
[*]/mnt/mythtv/d2/videos
[/LIST]

Then add these to the storage groups?

Is that all?

---

