# python-sqlite3
Это задания, выполнявшиеся в течение курса Using databases with Python.
https://www.coursera.org/learn/python-databases

_**005-Geoload.ipynb**_ является финальным проектом курса.

Что в нём происходит? - Из файла _where.data_ (где в начале нужно было вписать своё учебное заведение или место работы) считываются запросы (пример: 'Saint-Peterburg State University'), далее, используя API key, запросы отправляются в Google maps, ответы на эти запросы записываются в _geodata1.sqlite_. Идея использования здесь базы данных состоит в том, чтобы сделать процесс возобновляемым и не терять уже полученные данные: у Google maps есть ограничение на количество запросов в сутки, кроме того может прерваться интернет-соединение. Каждый ответ на запрос представляет собой:

{
   "html_attributions" : [],
   "results" : [
      {
         "formatted_address" : "University Embankment, 7/9, St Petersburg, Russia, 199034",
         "geometry" : {
            "location" : {
               "lat" : 59.941894,
               "lng" : 30.2989199
            },
            "viewport" : {
               "northeast" : {
                  "lat" : 59.94317928029151,
                  "lng" : 30.3007884302915
               },
               "southwest" : {
                  "lat" : 59.9404813197085,
                  "lng" : 30.2980904697085
               }
            }
         },
         "icon" : "https://maps.gstatic.com/mapfiles/place_api/icons/school-71.png",
         "id" : "41c9d8dd4e76616e03e3b06d37f3b1008048da71",
         "name" : "Saint Petersburg State University",
         "photos" : [
            {
               "height" : 3120,
               "html_attributions" : [
                  "\u003ca href=\"https://maps.google.com/maps/contrib/100523248215548318701/photos\"\u003eTsz Kit Zhuang\u003c/a\u003e"
               ],
               "photo_reference" : "CmRaAAAA5KCywowTH-uZyNwF1TCiNYcd6_o6z8nSUEKyIb9lQyXZHQayuOD3-K8paBfk1rVv0w_E5k8WZHrEP4FmTYHc-jFu5kzFBWA122RkMtygL4NRIjl6OlzNXMkCtrzpToqGEhAE6DEP7DuyyHYN1w8a-OKBGhThSXbTPBAxuSC6uru09rAg9nWSQw",
               "width" : 4160
            }
         ],
         "place_id" : "ChIJ6aX9PhgxlkYRP0Lp8GrRSqc",
         "rating" : 4.6,
         "reference" : "CmRSAAAARTk535j8wLZdfcg_a3XaHN2NpHMg8CadiEbZHdfoY9kwfbjAjRvbdT_3RVue7Gm3gVh2w4EuoNJdCGHf-noN0Yx5rrvsHrGzuqsjAUgwfGBF6a_zWPWBG2UFHMGb-P8BEhCzkaiHVaiu17nAPZkjmK8iGhTTt7PsRFCqiULQhwpeHgRq2wLcEQ",
         "types" : [ "university", "point_of_interest", "establishment" ]
      }
   ],
   "status" : "OK"
}

Этот ответ парсится, из него выделяются долгота, широта и название. Эти сведения записываются в _where.js_ (и _where.html_), который затем можно визуализировать в Google maps.
