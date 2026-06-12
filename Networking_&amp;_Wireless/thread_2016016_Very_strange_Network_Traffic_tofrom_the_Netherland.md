---
title: "Very strange Network Traffic to/from the Netherlands upon logging in"
date: 2012-07-04
forum: Networking &amp; Wireless
---

### Post by residualbit on 2012-07-04
On a whim, I decided to let wireshark do a few captures because I noticed some strange, quick spikes in network use when I first log in. Anyway, I almost immediately receive a TCP packet from 91.189.94.25 (seems to be based in the Netherlands.) It sends a FIN, ACK package to me on port 50398 and I send an ACK back to it on port 80. After this, the same handshake happens between my PC and 91.189.89.22, then nothing else. Any ideas as to what is going on?

---

### Post by msammels on 2012-07-04
I have no idea, but honestly, I got a lol. I went to the IP address you linked, and this was returned:

```
{
    "Ubuntu Music Search API": {
        "description": "The music search API is used to search
                        music catalogues to get lists of albums and
                        tracks for purchase. It is primarily used by
                        the music lens in Ubuntu itself.",
        "endpoints": {
            "/v1/search": {
                "parameters": {
                    "q": "The actual search query.",
                    "imagesize": "Size of linked cover art images in search results. 
                                  Defaults to 50. Chosen from list 33, 50, 52, 75, 100, 
                                  175, 180, 182, 200, 350, 500, 800. Some art may not 
                                  exist at high image sizes like 800.",
                    "genres": "Comma-separated list of genres (e.g., &#8220;rock,pop&#8221;).",
                    "grouping": "'1', to convert list of results into a dictionary
                                 of specific record types, keyed by kind of record.  
                                 Without grouping, [ artist alice, artist bob, album one ].
                                 With grouping, { artist: [alice, bob], album: [ one ] }.
                                 pagesize param and 'total' results are both per-type. ",
                    "page": "Page of results, for pagination. Defaults to 1.",
                    "pagesize": "Number of results returned per page. Defaults to 10.",
                    "decade": "Comma-separated list of decades to filter on for 
                               release date. Style is, e.g., &#8220;1980,1990&#8221;; allowed 
                               values are 1900-2020.",
                    "geo_store": "A two-letter country code designating the store to 
                                  search. Defaults to the appropriate country for the 
                                  requesting IP. Note that setting this will likely not 
                                  do what you want; if you get results for a store 
                                  inappropriate to your country, then you won't be 
                                  able to buy tracks from that store anyway, so you 
                                  likely shouldn't use this."
                },
                "example_output": {
                    "total": 19,
                    "pagesize": 10,
                    "page": 1
                    "results": [
                        {
                            "purchase_url": "u1ms://&#8230;/#url varies by source and geo store",
                            "artist": "The Rolling Stones",
                            "image": "http://cdn.7static.com/static/img/sleeveart/00/008/134/0000813486_50.jpg",
                            "title": "Exile On Main Street",
                            "source": "Ubuntu One Music Store",
                            "year": "2010",
                            "type": "album",
                            "web_purchase_url": ""
                        },
                        &#8230;
                    ]
                }
            }
        }
    }
}
```

But in all seriousness, have you tried:

```
whois 91.189.89.22
```

At all?

---

### Post by residualbit on 2012-07-04
Nah, I just looked it up on ARIN. Whois shows that the whole block is owned by Canonical, so I guess there's my answer. I suppose I overthought this one...Thanks!

---

