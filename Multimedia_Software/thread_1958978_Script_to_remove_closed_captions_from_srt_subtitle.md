---
title: "Script to remove closed captions from srt subtitle file"
date: 2012-04-15
forum: Multimedia Software
---

### Post by ki3456 on 2012-04-15
0
This script should remove closed captions from a srt subtitle file.
Captions are assumed to be enclosed in square brackets [...]

When two people speak in a subtitle their speech begins -space
When one person speaks in a subtitle there is no beginning -space
Captions are sometimes treated as a second speaker, sometimes not

Sed is used as it seems easiest and is common
The test subtitle file is Blithe Spirit

1
convert all new lines to tabs
cat bs.srt |tr '\n' '\t' > bs1.srt
or
sed -n '1{x;d};${H;x;s/\n/\t/g;p};{H}' bs.srt > bs1.srt

2
convert all instances of two consecutive tabs 
to a new line. (Each subtitle will be on one line.)

sed 's/\t\t/\n/g' bs1.srt > bs2.srt

3
remove initial line numbers
00:03:02,474 --> 00:03:03,975    Yes'm.

sed 's/[0-9]*\t//1' bs2.srt > bs3.srt

4
when a pattern matches tab[...]tab then 
[...]tab can safely be deleted.
00:05:22,239 --> 00:05:23,990    [Chuckling]    I love you, my love.
00:05:22,239 --> 00:05:23,990    I love you, my love.

sed  's/\t\[.*\]\t/\t/' bs3.srt > bs4.srt

5
when a pattern matches tab-space[...]tab-space then 
-space[...]tab-space  can safely be deleted.
00:06:39,983 --> 00:06:41,650    **[COLOR=Red]- [/COLOR]**[Doorbell Rings]    **[COLOR=Red]-[/COLOR]** That's probably the Bradmans.
00:06:39,983 --> 00:06:41,650    That's probably the Bradmans.

sed 's/\t- \[.*\]\t- /\t/' bs4.srt > bs5.srt

6
when a pattern matches tab[...]newline then 
tab[...] can safely be deleted.
00:03:47,352 --> 00:03:49,729    [Birds Chirping]
00:03:47,352 --> 00:03:49,729

00:17:52,363 --> 00:17:54,990    Oh, be good. There's a dear child.    [Clears Throat]
00:17:52,363 --> 00:17:54,990    Oh, be good. There's a dear child.

sed 's/\t\[.*\]$//' bs5.srt > bs6.srt

7
when the pattern matches no tabs then whole line
can safely be deleted. (blank subtitle)
00:03:47,352 --> 00:03:49,729

sed '/\t/!d' bs6.srt > bs7.srt

8
when a pattern matches -space[...]space then 
space[...] can safely be deleted
00:21:18,069 --> 00:21:20,695    - [Ruth] What's the matter with you?    - You must have heard that.
00:21:18,069 --> 00:21:20,695    - What's the matter with you?    - You must have heard that.

sed 's/- \[.*\] /- /' bs7.srt >bs8.srt

9
when a pattern matches tab-space[...]newline then 
tab-space[...] can safely be deleted
00:36:36,069 --> 00:36:37,444    [COLOR=Red]**-**[/COLOR] It isn't.    - [Cup Clatters]
00:36:36,069 --> 00:36:37,444 [COLOR=Red]**-** [/COLOR]It isn't.

sed 's/\t- \[.*\]$//' bs8.srt > bs9.srt

10
when a pattern matches [...]spaceORtab then 
[...]spaceORtab can safely be deleted
00:55:29,702 --> 00:55:33,663    [Clicks Tongue] You know, Charles,    she's absolutely ruined this room.
00:55:29,702 --> 00:55:33,663    You know, Charles,    she's absolutely ruined this room.

01:30:49,361 --> 01:30:51,612    Splendid! [Claps Hands]    Hurrah! We've done it.
01:30:49,361 --> 01:30:51,612    Splendid! Hurrah! We've done it.

sed 's/\[.*\] \|\[.*\]\t//' bs9.srt > bs10.srt

11
add line number and tab to beginning of line

sed = bs10.srt | sed 'N;s/\n/\t/' > bs11.srt

12
add extra new line for each line present

sed '/.*$/G'  bs11.srt > bs12.srt

13
replace all tabs with new lines

sed 's/\t/\n/g' bs12.srt > bs13.srt

14
display all lines that match [...]  (Missed captions.)
&#9834;&#9834; [Band: "Always"]
&#9834;&#9834; ["Always"]
- &#9834;&#9834; [Continues, Indistinct]

sed '/\[.*\]/!d' bs.srt > bs14.srt 

15
script for in-place caption removal
```
#!/bin/bash

find . -type f | grep .srt$ | while read file
do
title=`basename "$file" .srt`
sed -i -n '1{x;d};${H;x;s/\n/\t/g;p};{H}' "$file"
sed -i 's/\t\t/\n/g' "$file"
sed -i 's/[0-9]*\t//1' "$file"
sed -i 's/\t\[.*\]\t/\t/' "$file"
sed -i 's/\t- \[.*\]\t- /\t/' "$file"
sed -i 's/\t\[.*\]$//' "$file"
sed -i '/\t/!d' "$file"
sed -i 's/- \[.*\] /- /' "$file"
sed -i 's/\t- \[.*\]$//' "$file"
sed -i 's/\[.*\] \|\[.*\]\t//' "$file"
#sed = "$file" | sed -i 'N;s/\n/\t/'
sed -i '/./=' "$file" 
sed -i '/./N; s/\n/\t/' "$file"
sed -i '/.*$/G'  "$file"
sed -i 's/\t/\n/g' "$file"
sed '/\[.*\]/!d' "$file" > "$title".errors
done
```

---

