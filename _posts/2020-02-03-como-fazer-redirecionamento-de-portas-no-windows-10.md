---
layout: post
title: "Como fazer redirecionamento de portas no Windows 10"
date: 2020-02-03 09:46:42.000000000 -03:00
published: true
---

Já precisou fazer um redirecionamento de portas no Windows? Por acaso você já usou Docker Toolbox, e queria saber 
como evitar o uso do `192.168.99.100`? Hoje eu aprendi que dá pra usar o comando `netsh` pra isso. 

Acesse o Powershell como administrador, e digite

{% highlight powershell %}
netsh interface portproxy add v4tov4 listenport=80 listenaddress=127.0.0.1 connectport=80 connectaddress=192.168.99.100
{% endhighlight %}

Para saber se a regra foi aplicada, execute 

{% highlight powershell %}
netsh interface portproxy show all
{% endhighlight %}

Quer remover a regra?

{% highlight powershell %}
netsh interface portproxy delete v4tov4 listenport=80 listenaddress=127.0.0.1
{% endhighlight %}
