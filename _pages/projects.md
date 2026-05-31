---
layout: page
title: Research
permalink: /projects/
description: 
nav: true
nav_order: 3
display_categories: [Research Theme]
horizontal: false
---

<!-- pages/projects.md -->
<div class="projects">
<div style="
  max-width: 950px;
  margin: 0 auto 30px auto;
  padding: 20px 30px;
  background-color: rgba(74,144,226,0.05);
  border-radius: 8px;
">

  <h3 style="margin-top:0;">Vision</h3>

  <p style="font-size:1.15rem; line-height:1.8;">
    The goal of my research group <strong>Socially Responsible Intelligent Systems</strong> is to develop
    transparent, trustworthy, and human-centered AI models. Our research spans
    explainable AI, trustworthy foundation models, human-centered intelligent systems,
    and AI for social impact, with the goal of ensuring that advances in AI lead to
    meaningful benefits for individuals, communities, and society.
  </p>

</div>
<div align="center">
 
<video width="640" controls>
  <source src="/assets/video/short.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
</div>
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
