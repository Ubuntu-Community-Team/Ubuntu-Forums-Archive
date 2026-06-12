---
title: "dns wildcards and domain suffix"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by debianbryan on 2010-10-14
i tried to perform my due diligence and rtfm but came up dry.

i'm successfully getting *.foo.example.local to resolve with bind, but i find that i have to use the fqdn in order to resolve, both in ubuntu and in windows.  if i try to resolve *.foo, ubuntu won't automatically append the domain suffix, even though the search and domain directives are present in resolv.conf.  again, same goes for windows too.

at first i thought it might be a bind configuration issue and that i should create a separate zone for the foo.example.local subdomain, but the fact is *.foo.example.local resolves just fine, ubuntu just doesn't append the domain suffix.  there are other a records in the example.local domain that resolve fine using both fqdn and not.

---

