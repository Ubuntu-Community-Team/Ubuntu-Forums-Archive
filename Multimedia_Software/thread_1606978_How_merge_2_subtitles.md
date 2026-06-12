---
title: "How merge 2 subtitles?"
date: 2010-10-27
forum: Multimedia Software
---

### Post by marquinos on 2010-10-27
Hi! Can I do this?
subtitle1.srt + subtitle2.srt > final_subtitle.srt
I can't find a solution.

I want watch a movie with a subtitle in 2 languages, one line for the subtitle1 and another line for the subtitle2. With this I will read the foreign language (for learn that lenguage) and if I don't understand read my native language.

Thanks in advance!

Note: I don't like embed one subtitle into the movie and read the second on live. I want play the 2 subtitles or a merge of them.

---

### Post by lovinglinux on 2010-10-27
I don't think you can merge subtitles in such way, but you can use mkvtoolnix-gui to mux both subtitles with the video stream (not embedded) and then select one as primary and the other as secondary when playing. I never tried this tho, so I don't know which player can display both primary and secondary subtitles. Perhaps VlC or smplayer.

---

### Post by marquinos on 2010-10-27
I was thinking in a player, an application or a script.
I tried all players in the repositories and I didn't find a solution.

---

### Post by andrew.46 on 2010-10-28
Hi marquinos,

> **marquinos said:**
> Hi! Can I do this?
subtitle1.srt + subtitle2.srt > final_subtitle.srt
I can't find a solution.

I want watch a movie with a subtitle in 2 languages, one line for the subtitle1 and another line for the subtitle2. With this I will read the foreign language (for learn that lenguage) and if I don't understand read my native language.

If you open the files with a text editor you will see that this is possible with simple manual editing + a good deal of copying and pasting :).

Andrew

---

### Post by marquinos on 2010-10-28
@andrew.46: Please, no!!! xD hahahaha
It isn't only a "merge", the times must be [COLOR=#000000]overlapping in a correct time/text.[/COLOR]

---

### Post by andrew.46 on 2010-10-28
Hi marquinos,

> **marquinos said:**
>  the times must be [COLOR=#000000]overlapping in a correct time/text.[/COLOR]

But surely if you have 2 srt files for the same movie the timestamps will be almost exactly the same, just the text will be a different language?

Andrew

---

### Post by aeiah on 2010-10-28
have you tried gnome-subtitles?


you might be best seeing if a video player will just play both subtitles at the same time for you. perhaps vlc can do this.

---

### Post by marquinos on 2010-10-28
Is *more *probably that the time be different between 2 subtitles ;)
VLC hasn't this feature.

---

### Post by matrixnis on 2011-01-18
there is a free software caled subtitle workshop has option for merge subtitles...with him you can edit it later or adjust ofset

---

### Post by SeijiSensei on 2011-01-18
Many anime fansubbers use [Aegisub]("http://www.aegisub.org/") to generate [SSA/A**]("http://en.wikipedia.org/wiki/SubStation_Alpha") subtitles.  Maybe that will help.

---

### Post by t0x1 on 2012-05-06
Hi,

I'm using this online free tool : [http://www.srtmerger.org/en/](http://www.srtmerger.org/en/)

It merges the file regardless of the timestamp of each file (they don't have to be perfectly aligned). However, it only takes .SRT format files as input.

---

### Post by ki3456 on 2012-05-06
```

#!/usr/bin/awk -f

# this script should merge two srt subtitle files. 
# The first file will be output with times and text unchanged.
# The second file text will be merged _if_ start time of first file subtitle
# is between start and finish of second file's subtitle.
# 
# The script can't handle carriage returns.
# If the input files have carriage returns
# then remove them with the command: tr -d '\r' < input_cr > output_no_cr

BEGIN { FS = "[ :,]";current_file=""}
{if (current_file != FILENAME) {
    first_file=current_file;
    current_file=FILENAME;
    first_file_nr=current_nr;
    current_nr=0
    } 
}
{if ($0 != "") 
    {if ($0 ~ "-->") {
        start_time_ms  = ($1*3600000 + $2*60000 + $3*1000 + $4);
        finish_time_ms = ($6*3600000 + $7*60000 + $8*1000 + $9);
        start[current_file "," current_nr] = start_time_ms;
        finish[current_file "," current_nr] = finish_time_ms;
        time[current_file "," current_nr] = $0;
        }
    else text[current_file "," current_nr]=(text[current_file "," current_nr] "\t" $0) 
    }
}
{if ($0 == "") current_nr+=1}
END {
#remove line numbers from text
{for (x in text) {     
    str=text[x]; 
    str=substr(str,index(str,"\t")+1,length(str));
    str=substr(str,index(str,"\t")+1,length(str));
    text[x] = str;
    }
}
#add translation text where times overlap
{for (i=0;i<=first_file_nr;i++) { 
    if ((first_file "," i) in text)    {
        first_file_start=start[first_file "," i]; 
        {for (j=0;j<=current_nr;j++) { 
            if ((current_file "," j) in text) {
                current_file_start=start[current_file "," j];
                current_file_finish=finish[current_file "," j];
    {if (first_file_start>=current_file_start && first_file_start<current_file_finish)
    text[first_file "," i] = text[first_file "," i] "\t" text[current_file "," j] }
                }
            }
        }
        }
    }
}
# add subtitle times to text
{for (x in text) text[x] = time[x] "\t" text[x] }
# add subtitle numbers to text
n = 1;
{ for (i=0;i<=first_file_nr;i++)
    {if ((first_file "," i) in text)
        text[first_file "," i] = n++ "\t" text[first_file "," i];
    } 
}
# convert tabs to new lines
{for (x in text){ 
    str=text[x];
    n=split(str,array,"\t");
    str="";
    for (i=1;i<=n;i++) { str=(str array[i] "\n")}
    text[x]=str
    }    
}
# output merged file
{for (i=0;i<=first_file_nr;i++) 
    { if ((first_file "," i) in text) { print text[first_file "," i]}}
}

{if (first_file_nr=="") {
    {print "..............................................................."}
    {print "No merge file provided; Please provide two files for merge"}
    {print "Usage: ./merge_srt.awk file1.srt file2.srt > file1.merged.srt"}
    {print "..............................................................."}
    }
}
}

```

---

