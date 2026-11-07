# 📊 Análisis de Valoraciones de Videojuegos y Decisiones de Inversión (2011-2019)

## 📌 Descripción del Proyecto
Este proyecto consiste en el desarrollo de un **Dashboard analítico e interactivo en Power BI** orientado a proporcionar inteligencia de negocio para empresas o grupos de inversión interesados en el sector de los videojuegos. Se analizó un dataset con las valoraciones (de usuarios y críticos de Metacritic) de los títulos lanzados durante la octava generación de consolas (período 2011-2019), abarcando un volumen de **5,655 videojuegos**.

El objetivo principal fue aplicar metodologías de Business Intelligence para identificar patrones de éxito comercial y de audiencia, determinando los géneros más rentables y recomendando el **Top 5 de desarrolladoras** más viables para futuras inversiones.

---

## 💡 Hipótesis de Negocio
1. Determinar qué compañías desarrolladoras lanzaron la mayor cantidad de videojuegos con valoraciones positivas por parte de los usuarios y comprobar si este comportamiento se correlaciona con la opinión de los críticos especializados.
2. Identificar el género de videojuegos más exitoso de la octava generación para optimizar la toma de decisiones financieras en nuevos desarrollos.
3. Proponer un modelo de recomendación basado en datos para guiar estrategias de inversión eficientes.

---

## 🛠️ Arquitectura de Datos y Modelado
A partir de los archivos planos de origen, se ejecutó un proceso de limpieza, transformación y estructuración de datos, migrando la información hacia un **Modelado Estrella (Star Schema)** para optimizar el rendimiento de las consultas y la segmentación en Power BI.

### Componentes del Modelo:
*   **Tabla de Hechos (Fact Table):** `JUEGO` (Contiene las métricas operativas, fechas de lanzamiento, Metascore y User Score).
*   **Tablas Dimensionales (Dim Tables):** `DEVELOPER`, `GÉNERO`, `PLATAFORMA`, `TIPO_PLATAFORMA` y `RATING`.
*   **Tabla de Tiempo:** Se generó una tabla `CALENDARIO` dinámica mediante DAX para permitir análisis temporales (apertura por Año, Trimestre, Mes y Día).

<img width="1148" height="928" alt="image" src="https://github.com/user-attachments/assets/c884231a-7049-42ef-8a15-e1acbce8a8cf" />

<img width="1311" height="800" alt="image" src="https://github.com/user-attachments/assets/79f86f4e-9152-4928-bedb-74f430d5f228" />


---

## 🧮 Inteligencia de Negocio (Modelado DAX)
Se implementaron medidas calculadas optimizadas para estructurar las visualizaciones y extraer los indicadores clave de rendimiento (KPIs) del negocio:

*   **Total de Videojuegos:** 
    ```DAX
    Total videojuegos = COUNT(JUEGO[ID_JUEGO])
    ```
*   **Promedio General de Usuarios (UserScore):**
    ```DAX
    Promedio general usuario = SUM(JUEGO[USER_SCORE]) / COUNT(JUEGO[ID_JUEGO])
    ```
*   **Promedio General de la Crítica (MetaScore):**
    ```DAX
    Promedio general metacritic = SUM(JUEGO[METASCORE]) / COUNT(JUEGO[ID_JUEGO])
    ```
*   **Distribución Promedio de Juegos por Plataforma:**
    ```DAX
    Promedio de Juegos por plataforma = AVERAGEX(KEEPFILTERS(VALUES('JUEGO'[ID_PLATAFORMA])), CALCULATE(COUNTA('JUEGO'[ID_JUEGO])))
    ```

---

## 🖥️ Visualización y Funcionalidad del Dashboard
El tablero cuenta con una interfaz intuitiva con navegación libre y capacidades de filtrado avanzado:
1.  **Menú de Inicio:** Sistema de botones interactivos para la navegación entre solapas temáticas.
2.  **Análisis por Plataforma:** Gráficos de distribución (torta y anillo) según tipo de plataforma (Hogar, Portátil, Híbrida) y volumen temporal.
3.  **Análisis de Géneros:** Segmentaciones cruzadas e histogramas apilados para contrastar el comportamiento de lanzamientos frente a las valoraciones recibidas.
4.  **Módulo de Valoraciones (Usuarios vs. Metacritic):** Vista enfocada al ranking detallado de desarrolladoras y títulos específicos.

<img width="558" height="308" alt="image" src="https://github.com/user-attachments/assets/5903f16c-aa4c-4e53-b114-56d5740c755e" />

<img width="566" height="322" alt="image" src="https://github.com/user-attachments/assets/ef023691-0f02-4fdb-a907-212d673602ac" />

<img width="656" height="366" alt="image" src="https://github.com/user-attachments/assets/edb950e3-ece0-44b1-b2f5-56c50639e30b" />

<img width="661" height="366" alt="image" src="https://github.com/user-attachments/assets/b6aebaba-dbbc-41aa-a3c2-4dd32f80733e" />

<img width="654" height="369" alt="image" src="https://github.com/user-attachments/assets/d82efc04-2d3e-40f3-8107-bc804b228683" />

---

## 📈 Conclusiones Clave y Recomendaciones de Inversión

A partir del análisis descriptivo y exploratorio de los datos de la octava generación de consolas, se extrajeron los siguientes hallazgos estratégicos:

*   **Dominio de Plataformas:** Los entornos de **PC (1er lugar)**, **PS4 (2do lugar)** y **XONE (3er lugar)** concentran la mayor cantidad de títulos y volumen de usuarios activos, destacando la preferencia por experiencias "hogareñas" de juego.
*   **Género Más Exitoso:** El género **"City Building"** se posicionó como el mejor valorado y con mayor retención de audiencia, representando una apuesta segura para mitigar el riesgo financiero en fases de desarrollo.
*   **Análisis de Desarrolladoras (Top 3 de Consistencia):** Tanto el público como la crítica especializada coinciden de forma unánime en que **Telltale Games**, **Capcom** y **Nintendo** lideran en volumen de juegos altamente valorados positivamente.
*   **Títulos de Máximo Impacto:** **"The Witcher"** se corona como el juego con mayor valoración histórica por parte de los usuarios, mientras que **"Grand Theft Auto"** lidera las puntuaciones de la crítica profesional (Metacritic).

### 🎯 Recomendación Estratégica:
Para optimizar las carteras de inversión, se aconseja orientar los recursos financieros hacia desarrolladoras consolidadas dentro del top analizado (**Telltale Games / Capcom**) o apostar por la creación de propiedad intelectual enfocada en mecánicas de larga duración (tipo mundo abierto o construcción de ciudades) diseñadas específicamente para plataformas de hogar, donde el usuario valora la comodidad y la inmersión profunda en la narrativa.
