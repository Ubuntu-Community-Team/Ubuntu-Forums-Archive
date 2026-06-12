---
title: "[SOLVED] Video IMDB Description issue"
date: 2008-08-03
forum: Mythbuntu
---

### Post by amacmil on 2008-08-03
First of all thank you in advance for reading this post and providig any support or info.

I am relatively new to mythbuntu but have been using mythtv for a couple of years, great package and ubuntu is also awesome, never looked back since I have installed it.

Right the problem: I have several backed up copies of dvd and cd which I have stored in the correct places ..../video etc. How ever when I run the IMDB search within myth or through mythweb(post the fix) the system manages to retrieve the information and post it to the database however I seem to loose the Video description, I have done several searches but can not seem to find anyone else that has the problem. If anyone can help will be eternally grateful.

I am running mythbuntu 8.04.1 with minimal alterations, on a IBM netvista 1 gb ram.

If there are any commands I need to type to produce a log file please just tell me, I am still relatively new to ubuntu.

Thanks again for your help in advance.

---

### Post by Ohs0Ahxi on 2008-08-03
> **amacmil said:**
> First of all thank you in advance for reading this post and providig any support or info.

I am relatively new to mythbuntu but have been using mythtv for a couple of years, great package and ubuntu is also awesome, never looked back since I have installed it.

Right the problem: I have several backed up copies of dvd and cd which I have stored in the correct places ..../video etc. How ever when I run the IMDB search within myth or through mythweb(post the fix) the system manages to retrieve the information and post it to the database however I seem to loose the Video description, I have done several searches but can not seem to find anyone else that has the problem. If anyone can help will be eternally grateful.

I am running mythbuntu 8.04.1 with minimal alterations, on a IBM netvista 1 gb ram.

If there are any commands I need to type to produce a log file please just tell me, I am still relatively new to ubuntu.

Thanks again for your help in advance.

By video description do you mean the IMDB plot? If so then this should solve it;
In /usr/share/mythtv/mythvideo/scripts/

Open imdb.pl for editing and find the following line 
```
my $plot = parseBetween($response, ">Plot Outline:</h5> ", "</div>"); 
``` 
And change it to ```
my $plot = parseBetween($response, ">Plot:</h5>", "</div>");
```

Taken from [_This thread_](http://ubuntuforums.org/showthread.php?t=782124)

---

### Post by amacmil on 2008-08-03
Quality that has solved the little issue I had, goes to show when searching to ensure i use the right terminology.

Thank you again for your help this is definately better than MS...

---

### Post by Baka no Kami on 2008-10-15
For some reason when I changed that line all the script did was start adding "None" to the Plot field. Even when the IMDB entry did have a plot description.

I've been using a bulk update script to fill in IMDB data and it came with another copy of the imdb.pl

The section it had for getting plot info worked when pasted into the original imdb.pl script that installed with myth video.

```
   # parse plot
   my $plot = parseBetween($response, ">Plot Outline:</h5> ", "</div>");
   if (!$plot) {
      $plot = parseBetween($response, ">Plot Summary:</h5> ", "</div>");
   }
   if (!$plot) {
      $plot = parseBetween($response, ">Plot:</h5>", "</div>");
   }

   if ($plot) {
      # replace name links in plot (example 0388795)
      $plot =~ s/$name_link_pat/$1/g;

      # replace title links
      my $title_link_pat = qr!<a href="/title/[^"]*">([^<]*)</a>!m;
      $plot =~ s/$title_link_pat/$1/g;

      # plot ends at first remaining link
      my $plot_end = index($plot, "<a ");
      if ($plot_end != -1) {
         $plot = substr($plot, 0, $plot_end);
      }
      $plot = trim($plot);
   }
```

---

