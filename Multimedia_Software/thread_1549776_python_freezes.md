---
title: "python freezes"
date: 2010-08-10
forum: Multimedia Software
---

### Post by delurfangs on 2010-08-10
i am codeing my first game in python 
when i try to test my game it get to this part and suddenly starts takeing 100% of my cpu and i have to kill the processes the rest of the game runs fine any tips for a newb who is already feeling slightly over loaded? 

thanks in advanced 

```
 
    while (health > 0) and (skellyhp > 0): 
        loop = 0 
    if (health < 0) or (skellyhp < 0): 
        loop = 1 
    while loop == 0: 
         
        if "sword" in inventory: 
            print "you slash your sword at the skeleton..." 
            itembonus = 2 
        elif "staff" in inventory: 
            print "you wip your staff at the skelleton's head..." 
            itembonus = 2 
        elif "mace" in inventory: 
            print "you bring your mace crashing down..." 
            itembonus = 2  
        else: 
            print "you swing a right haymaker at the skelleton..." 
 
        chardmg = random.randrange(4) + itembonus 
 
         
        print "you deal " , chardmg, " points of damage!" 
        skellyhp -=chardmg 
        print "HP: ", health 
        print " skellys HP: ", skellyhp 
        raw_input()
```


Never mind i see what i did now i fell stupid this is what i get for staying up for 2 days looking at code then posting for help. 
but any advise for cleaning up this code would be appreciated

---

