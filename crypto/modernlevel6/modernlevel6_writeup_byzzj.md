# modernlevel6

## 由于题目所述，我们得到了密钥对，又因为我们知道fn和n的值相差不大

## 所以我们可以得到
e0*d0 == k* fn + 1
两边同时除以n 又因为 n～fn
所以有
e0*d0／n 约等于 k （比k小）

## 所以我们可以通过穷举求出fn

```python
from gmpy2 import *

e0 = 12579179311674880606263699553638970371892432345293207780859775189817653L
d0 = 466294326450449655113269604053072369085134095709355289497342511041733161318672772650225476238904690978642883878275259143802660800546784900944189504317191151064005649045320924493284360361954636441841041455061721010054858167985133144474359684686439988141690951535627668320213768462654762907273681135912221503676694453088416039218947406297417569185885903596486878036971044737390201051989997800334007152386986548462980343276856907302827211567980235720706363870628411109181695820793836812800103469177298864072037598596816578539605895556124186619276695453253847051323639894801714946389006686988732938843017689625928159415908327120124418409016744908077555225623858070964642224253467788060908754646868478658745402528967999090927111421275609429798789636421294204441339498614560225456565650297847320897800444670928308241215318430311598098784188926891040264927290177251036148545683626929561157869427951789890081886922991935401169207813239620466670792396236337997206841928454874559130280725956453713697747884297731904637445302805121331847097700531687811920266714360777047564675619697103557084314064712686383757989696932997782222493909008441044178924653449565735126831014595614058685689000618343372751726198051096665434668522972961986952591475373L
e = 65537
n = 628406889803254794657128366014346324845313568553742678907537772245227903820631319719191127163382313291886705635146572160356154905244794220406841160675659358122506089964463150205728274637985139701152237836635104271679928112069582690428104641259731022633759700016108531558282651418224722574948238730283397733217298825796642163614432909474270827000928696247239193317620967151454952524552777629380165049142464909145447255880702380995730745345674300906025060805530223990156589416606448920829845082495499712479649882935234160314625803309342816623982353471265173718183888091911337649813155749472834415191627631965459170012129551946273202696977390564426767828239364625547572078323098430826371490979543682835488759169858637474340238987890392460563577835121561955675695024398055761463123008063143860259287753744013430583196685896078855079628303408960496396830901995996677181438217659116998295000271956633050904327659054446070372720314057998064541716904183912399134353317720657671097605098078915691765296732827513252966030685767038482128833595392633648440061943720868284928157181588961473342755425122649737554375334378030240076581727271412144196253362154104390730463316350382283851901088053635105335601090041886880668319092637227230457740139151
ct = 384626788210113992539919421023941661424734480292506186324826344277314445384902276826659495009096621153289072622454957343184197050847932734644412524642500727895470730854236585316345616152504411563324609026538080885092661793849410843419604406957096772533463557362184082076967512264974215977453241967972522136497893630917629806855452674136666311128874298577437733572725610844363130703421627919621771639107602316463909413944574852419198954353651137248313081310303645827971159859656474939272945259624034231775715483480721014564449019603830278561555195601998489353368243082740883548804695629214973419948843002889540887708820173717763363330786201150152066267678686806707254974831214473432369249396605367564011063702861580833151793341270191848745902728468733883595886149415210573029671835212427398763900577488785799228236595760041877868960000011669442828943762265440760303364080023095110868408264086531897402843846525091059235371870907283687913817711674517599537064740494214376360614318915229350653705627110534820438198729859428305101813280233706073162143270636470754451588669463155343051433970563853752741227078729391110302760236500451124937786013907914065606938068264607485605662616529293703129135047387720576075492473877280173364996560521

k = e0*d0/n

while True:
    fn = (e0*d0 - 1)/k
    if fn*k + 1 == e0 * d0:
        break
    k+=1

d = invert(e,fn)

m = pow(ct,d,n)
print hex(m)[2:].decode('hex')
```
于是我们有了flag
## flag{there_are_just_too_many_rsa_issues_so_I_will_skip_some_of_them...}