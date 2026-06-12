---
title: "IMDB MPAA rating trouble"
date: 2008-08-03
forum: Mythbuntu
---

### Post by Shrynn on 2008-08-03
Hey guys, I'm new to MythTV so maybe I'm missing something. I just downloaded and installed Mythbuntu, and I'm still doing setup. The issue is that when I attempt to retrieve the Movie info from IMDB it didn't show MPAA rating or Plot info. 

I did some search here and updated the imdb.pl script with a new one and now the plots appear but the MPAA rating still does not...

I used the same script as others, but after searching these forums it seems that no one has this issue. Any ideas?

My MPAA line looks like this:
```
 # parse MPAA rating
   my $ratingcountry = "USA";
   my $movierating = trim(parseBetween($response, ">MPAA</a>:</h5>", "</div>"));
   if (!$movierating) {
       $movierating = parseBetween($response, ">Certification:</h5>", "</div>");
       $movierating = parseBetween($movierating, "certificates=$ratingcountry",
                                   "/a>");
       $movierating = parseBetween($movierating, ">", "<");
   }

```

I'm looking on the IMDB website and I'm not seeing the MPAA rating... Can someone confirm that the Ratings actually work with IMDB and MythTV?

---

