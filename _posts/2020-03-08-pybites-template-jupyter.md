---
keywords: fastai
description: "Resolver y realizar Test para PyBites"
title: PyBites Template for Exercises
toc: false
branch: master
badges: true
comments: true
categories: [python, pytest, jupyter, template, pybites]
nb_path: _notebooks/2020-03-08-pybites-template-jupyter.ipynb
layout: notebook
---

<!--
#################################################
### THIS FILE WAS AUTOGENERATED! DO NOT EDIT! ###
#################################################
# file to edit: _notebooks/2020-03-08-pybites-template-jupyter.ipynb
-->

<div class="container" id="notebook-container">
        
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Intro">Intro<a class="anchor-link" href="#Intro"> </a></h1><p>Este notebook se podrá usar como plantilla para resolver los ejercicios <a href="https://codechalleng.es/bites/">PyBites</a> de la plataforma <a href="https://codechalleng.es/">codechalleng.es</a></p>
<h2 id="Uso">Uso<a class="anchor-link" href="#Uso"> </a></h2><ul>
<li>En la PyBites Platform selecciona un Bite Exercise y haz clic en <strong>GITHUB -&gt; DOWNLOAD BITE</strong></li>
<li>Copiar este notebook a la carpeta <strong>pybites_biteXYZ</strong>, ejemplo: pybites_bite130.</li>
<li>Abrir el notebook y ejecutar todas las celdas ( <strong>Cell -&gt; Run All</strong> ).</li>
<li>Cargar (<strong>%load</strong>) el módulo python ejecutando la segunda celda (más abajo) para resolver ejercicio.</li>
<li>Escribir (<strong>%%writefile</strong>) al módulo python la respuesta al ejercicio. Leer la Nota para más detalles.</li>
<li>Ejecutar las pruebas, <strong>descomentar</strong> y ejecutar la última celda utilizando PyTest.
{% include note.html content='El comando mágico de celda %%writefile debes estar en la primera línea, borra el comentario generado por el comando mágico de línea %load .' %}</li>
</ul>

</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">pathlib</span> <span class="kn">import</span> <span class="n">Path</span>
<span class="kn">from</span> <span class="nn">IPython.display</span> <span class="kn">import</span> <span class="n">HTML</span>

<span class="n">BITE</span> <span class="o">=</span> <span class="s2">&quot;./bite.html&quot;</span>
<span class="n">files</span> <span class="o">=</span> <span class="n">Path</span><span class="p">()</span><span class="o">.</span><span class="n">glob</span><span class="p">(</span><span class="s2">&quot;test_*.py&quot;</span><span class="p">)</span>
<span class="k">try</span><span class="p">:</span>
    <span class="n">PYBITES</span> <span class="o">=</span> <span class="nb">next</span><span class="p">(</span><span class="n">files</span><span class="p">)</span>
<span class="k">except</span> <span class="ne">StopIteration</span><span class="p">:</span>
    <span class="k">raise</span><span class="p">(</span><span class="ne">Exception</span><span class="p">(</span><span class="s2">&quot;PYBITES_TEMPLATE &quot;</span> <span class="o">+</span>
                    <span class="s2">&quot;must be inside pybite_biteXYZ &quot;</span> <span class="o">+</span>
                    <span class="s2">&quot;folder with a test file&quot;</span><span class="p">))</span>

<span class="k">if</span> <span class="n">PYBITES</span><span class="p">:</span>
    <span class="n">PYBITES</span> <span class="o">=</span> <span class="nb">str</span><span class="p">(</span><span class="n">PYBITES</span><span class="p">)</span><span class="o">.</span><span class="n">split</span><span class="p">(</span><span class="s2">&quot;test_&quot;</span><span class="p">)[</span><span class="mi">1</span><span class="p">]</span>

<span class="k">def</span> <span class="nf">write_imports</span><span class="p">(</span><span class="n">file</span><span class="o">=</span><span class="s2">&quot;__imports.py&quot;</span><span class="p">,</span> <span class="n">code</span><span class="o">=</span><span class="kc">None</span><span class="p">,</span>
                  <span class="n">mode</span><span class="o">=</span><span class="s2">&quot;w&quot;</span><span class="p">,</span> <span class="n">seek</span><span class="o">=</span><span class="mi">0</span><span class="p">):</span>
    <span class="k">with</span> <span class="nb">open</span><span class="p">(</span><span class="n">file</span><span class="p">,</span> <span class="n">mode</span><span class="p">)</span> <span class="k">as</span> <span class="n">pb</span><span class="p">:</span>
        <span class="n">lines</span> <span class="o">=</span> <span class="s2">&quot;&quot;</span>
        <span class="k">if</span> <span class="s2">&quot;r&quot;</span> <span class="ow">in</span> <span class="n">mode</span><span class="p">:</span>
            <span class="n">lines</span> <span class="o">=</span> <span class="s2">&quot;&quot;</span><span class="o">.</span><span class="n">join</span><span class="p">(</span><span class="n">pb</span><span class="o">.</span><span class="n">readlines</span><span class="p">())</span>
        <span class="n">lines</span> <span class="o">=</span> <span class="sa">f</span><span class="s2">&quot;</span><span class="si">{</span><span class="n">code</span><span class="si">}</span><span class="se">\n</span><span class="si">{</span><span class="n">lines</span><span class="si">}</span><span class="s2">&quot;</span>
        <span class="n">pb</span><span class="o">.</span><span class="n">seek</span><span class="p">(</span><span class="n">seek</span><span class="p">)</span>
        <span class="n">pb</span><span class="o">.</span><span class="n">truncate</span><span class="p">()</span>
        <span class="n">pb</span><span class="o">.</span><span class="n">writelines</span><span class="p">(</span><span class="n">lines</span><span class="p">)</span>

<span class="n">HTML</span><span class="p">(</span><span class="n">filename</span><span class="o">=</span><span class="n">BITE</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">CODE</span> <span class="o">=</span> <span class="sa">f</span><span class="s2">&quot;%load </span><span class="si">{</span><span class="n">PYBITES</span><span class="si">}</span><span class="s2">&quot;</span>
<span class="n">write_imports</span><span class="p">(</span><span class="n">code</span><span class="o">=</span><span class="n">CODE</span><span class="p">)</span>
<span class="n">CODE</span> <span class="o">=</span> <span class="sa">f</span><span class="s2">&quot;%%writefile </span><span class="si">{</span><span class="n">PYBITES</span><span class="si">}</span><span class="s2">&quot;</span>
<span class="n">write_imports</span><span class="p">(</span><span class="n">file</span><span class="o">=</span><span class="n">PYBITES</span><span class="p">,</span> <span class="n">code</span><span class="o">=</span><span class="n">CODE</span><span class="p">,</span>
              <span class="n">mode</span><span class="o">=</span><span class="s2">&quot;r+&quot;</span><span class="p">,</span> <span class="n">seek</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
<span class="o">%</span><span class="k">load</span> __imports.py
</pre></div>

    </div>
</div>
</div>

</div>
    {% endraw %}

    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span> 
</pre></div>

    </div>
</div>
</div>

</div>
    {% endraw %}

</div>
 

